## Physical Security
It is evident that we need to ensure physical security for our computer systems; however, in the unlikely event that physical security is breached, we need to provide additional layers of protection. Many BIOS and UEFI firmware allows you to add a boot password. This password will prevent unauthorised users from booting the system. However, this can only be used for personal systems; it won’t make sense to use it on servers as this will require someone to be physically present to supply the boot password.
We can consider adding a GRUB password depending on the Linux system we want to protect. Many tools help achieve that. One tool is `grub2-mkpasswd-pbkdf2`, which prompts you to input your password twice and generates a hash for you. The resulting hash should be added to the appropriate configuration file depending on the Linux distribution (examples: [Fedora](https://docs.fedoraproject.org/en-US/fedora-coreos/grub-password/) and [Ubuntu](https://help.ubuntu.com/community/Grub2/Passwords)). This configuration would prevent unauthorised users from resetting your root password. It will require the user to supply a password to access advanced boot configurations via GRUB, including logging in with root access.

## Filesystem Partitioning and Encryption
There are various software systems and tools that provide encryption to Linux systems. Since many modern Linux distributions ship with LUKS (Linux Unified Key Setup). When a partition is encrypted with LUKS, the disk layout would look as:
- **LUKS phdr**: It stands for _LUKS Partition Header_. LUKS phdr stores information about the UUID (Universally Unique Identifier), the used cipher, the cipher mode, the key length, and the checksum of the master key.
- **KM**: KM stands for _Key Material_, where we have KM1, KM2, …, KM8. Each key material section is associated with a key slot, which can be indicated as active in the LUKS phdr. When the key slot is active, the associated key material section contains a copy of the master key encrypted with a user's password. In other words, we might have the master key encrypted with the first user's password and saved in KM1, encrypted with the second user's password and saved in KM2, and so on.
- **Bulk Data**: This refers to the data encrypted by the master key. The master key is saved and encrypted by the user's password in a key material section.

LUKS works with different ciphers and cipher modes.
Most distributions let you encrypt a drive using a graphical interface. However, if you would like to set up LUKS from the command line, the steps are along these lines:

- Install `cryptsetup-luks`. (You can issue `apt install cryptsetup`, `yum install cryptsetup-luks` or `dnf install cryptsetup-luks` for Ubuntu/Debian, RHEL/Cent OS, and Fedora, respectively.)
- Confirm the partition name using `fdisk -l`, `lsblk` or `blkid`. (Create a partition using `fdisk` if necessary.)
- Set up the partition for LUKS encryption: `cryptsetup -y -v luksFormat /dev/sdb1`. (Replace `/dev/sdb1` with the partition name you want to encrypt.)
- Create a mapping to access the partition: `cryptsetup luksOpen /dev/sdb1 EDCdrive`.
- Confirm mapping details: `ls -l /dev/mapper/EDCdrive` and `cryptsetup -v status EDCdrive`.
- Overwrite existing data with zero: `dd if=/dev/zero of=/dev/mapper/EDCdrive`.
- Format the partition: `mkfs.ext4 /dev/mapper/EDCdrive -L "Strategos USB"`.
- Mount it and start using it like a usual partition: `mount /dev/mapper/EDCdrive /media/secure-USB`.

## Firewall
he first Linux firewall was a packet filtering firewall, i.e., a stateless firewall. A stateless firewall can inspect certain fields in the IP and TCP/UDP headers to decide upon a packet but does not maintain information about ongoing TCP connections. As a result, a packet can manipulate a few TCP flags to appear as if it is part of an ongoing connection and evade certain restrictions. Current Linux firewalls are stateful firewalls; they keep track of ongoing connections and restrict packets based on specific fields in the IP and TCP/UDP headers and based on whether the packet is part of an ongoing connection.

The IP header fields that find their way into the firewall rules are:

1. Source IP address
2. Destination IP address

The TCP/UDP header fields that are of primary concern for firewall rules are:

1. Source TCP/UDP port
2. Destination TCP/UDP port

It is worth noting that it is impossible to allow and deny packets based on the process but instead on the port number. If you want the web browser to access the web, you must allow the respective ports, such as ports 80 and 443. This limitation differs from MS Windows’ built-in firewall, which can restrict and allow traffic per application.

On a Linux system, a solution such as [SELinux](https://github.com/SELinuxProject) or [AppArmor](https://www.apparmor.net/) can be used for more granular control over processes and their network access. For example, we can allow only the `/usr/bin/apache2` binary to use ports 80 and 443 while preventing any other binary from doing so on the underlying system. Both tools enforce access control policies based on the specific process or binary, providing a more comprehensive way to secure a Linux system.
### Netfilter

At the very core, we have netfilter. The netfilter project provides packet-filtering software for the Linux kernel 2.4.x and later versions. The netfilter hooks require a front-end such as `iptables` or `nftables` to manage.
### iptables

As a front-end, iptables provides the user-space command line tools to configure the packet filtering rule set using the netfilter hooks. For filtering the traffic, iptables has the following default chains:

- **Input**: This chain applies to the packets incoming to the firewall.
- **Output**: This chain applies to the packets outgoing from the firewall.
- **Forward** This chain applies to the packets routed through the system.

Let’s say that we want to be able to access the SSH server on our system remotely. For the SSH server to be able to communicate with the world, we need two things:

1. Accept incoming packets to TCP port 22.
2. Accept outgoing packets from TCP port 22.

Let’s translate the above two requirements into `iptables` commands:

`iptables -A INPUT -p tcp --dport 22 -j ACCEPT`

- `-A INPUT` appends to the INPUT chain, i.e., packets destined for the system.
- `-p tcp --dport 22` applies to TCP protocol with destination port 22.
- `-j ACCEPT` specifies (jump to) target rule ACCEPT.

`iptables -A OUTPUT -p tcp --sport 22 -j ACCEPT`

- `-A OUTPUT` append to the OUTPUT chain, i.e., packets leaving the system.
- `-p tcp --sport 22` applies to TCP protocol with source port 22.

Let’s say you only want to allow traffic to the local SSH server and block everything else. In this case, you need to add two more rules to set the default behaviour of your firewall:

- `iptables -A INPUT -j DROP` to block all incoming traffic not allowed in previous rules.
- `iptables -A OUTPUT -j DROP` to block all outgoing traffic not allowed in previous rules.
### nftables

nftables is supported in Kernel 3.13 and later, adding various improvements over iptables, particularly in scalability and performance.
Unlike iptables, nftables start with no tables or chains. We need to add the necessary tables and chains before adding rules. To begin, we will create a table, `fwfilter`.

`nft add table fwfilter`

- `add` is used to add a table. Other commands include `delete` to delete a table, `list` to list the chains and rules in a table, and `flush` to clear all chains and rules from a table.
- `table TABLE_NAME` is used to specify the name of the table we want to create or work on.

In our newly created table, `fwfilter`, we will add an _input_ chain and an _output_ chain for incoming and outgoing packets, respectively.

- `nft add chain fwfilter fwinput { type filter hook input priority 0 \; }`
- `nft add chain fwfilter fwoutput { type filter hook output priority 0 \; }`

The above two commands add two chains to the table `fwfilter`:

- `fwinput` is the input chain. It is of type `filter` and applies to the input hook.
- `fwoutput` is the output chain. It is of type `filter` and applies to the output hook.

With the two chains created within our table, we can add the necessary rule to allow SSH traffic. The following two rules are added to the table `fwfilter` to the chains `fwinput` and `fwoutput`, respectively:

- `nft add fwfilter fwinput tcp dport 22 accept` accepts TCP traffic to the local system’s destination port 22.
- `nft add fwfilter fwoutput tcp sport 22 accept` accepts TCP traffic from the local system’s source port 22.

We can check the shape of the `fwfilter` table using the command `nft list table fwfilter`

### UFW
UFW stands for uncomplicated firewall. Let’s see how it stands for its promise of being _uncomplicated_. We will allow SSH traffic. This firewall rule can be achieved through one of the following commands:

`ufw allow 22/tcp`

It configures the firewall to `allow` traffic to TCP port 22. We can confirm our settings with the command `ufw status`.
### Firewall Policy
Before configuring a firewall, you need to decide upon the firewall policy. You might be the decision maker regarding the firewall policy or an enforcer of an existing security policy that covers firewall configuration. It all depends on the system you are protecting.

We will not go into security policies as this is outside the scope of this room. We will mention that the two main approaches are:

- Block everything and allow certain exceptions.
- Allow everything and block certain exceptions.

## Securing User Accounts
### Use sudo

To avoid logging in as `root`, the better approach would be to have an account -created for administrative purposes- added to the _sudoers_, i.e. group who can use the `sudo` command. `sudo` stands for Super User Do and it should precede any command that requires `root` privileges.

Depending on the Linux distribution, we can add a user to the sudoers group in the following ways. Some distributions, such as Debian and Ubuntu, call the sudoers group `sudo`. In this case, you would need to issue the following command:

`usermod -aG sudo username`

- `usermod` modifies a user account.
- `-aG` appends to group.
- `sudo` is the name of the group of users who can use `sudo` on Debian-based distributions.
- `username` is the name of the user account you want to modify.
Other distributions, such as RedHat and Fedora, refer to the sudoers group as `wheel`. Consequently, you would need to issue the following command:

`usermod -aG wheel username`

### Disable root
Once you have created an account for administrative purposes and added it to the `sudo`/`wheel` group, you might consider disabling the `root` account. A straightforward way is to modify the `/etc/passwd` and change the `root` shell to `/sbin/nologin`. In other words, edit `/etc/passwd` and change the line `root:x:0:0:root:/root:/bin/bash` to `root:x:0:0:root:/root:/sbin/nologin`.
### Enforce a Strong Password Policy
The `libpwquality` library provides many options for password constraints. The configuration file can be found at:
- `/etc/security/pwquality.conf` on RedHat and Fedora
- `/etc/pam.d/common-password` on Debian and Ubuntu. You can install it using `apt-get install libpam-pwquality`
Here are a few example options:
- `difok` allows you to specify the number of characters in the new password that were not present in the old password.
- `minlen` sets the minimum allowed length for new passwords.
- `minclass` specifies the minimum number of required classes of characters; a class can be uppercase, lowercase, and digits, among others.
- `badwords` provides a space-separated list of words that must not be contained in the chosen password.
- `retry=N` prompts the user `N` times before returning an error.
### Disable Unused Accounts
As part of system maintenance, it is vital to disable user accounts that no longer need access to the system in question. For instance, these users might have moved to another department or quit the company.
You can disable a user account in the same way we would disable the root account. An easy way would be to edit the `/etc/passwd` file and set the shell of the user account we want to disable to `/sbin/nologin`.
Let’s say that we want to disable the account of the user Michael with username `michael`.

- Enabled account: `michael:x:1000:1000:Michael:/home/michael:/usr/bin/fish`
- Disabled account: `michael:x:1000:1000:Michael:/home/michael:/sbin/nologin`

We should do the same for local services. In other words, we should set the shell to `sbin/nologin` for all the local service accounts such as `www-data`, `mongo`, and `nginx`, to name a few. The reason is that these services need accounts to run on the system but would never need to log in and access a shell. Any of these services could perhaps have an RCE (Remote Code Execution) vulnerability, and by setting the shell to `nologin`, we can at least prevent interactive logins for the account of the affected service.

## Software and Service
### Disable Unnecessary Services
One of the easiest ways to improve your security posture is by removing or disabling unneeded services and packages.
### Block Unneeded Network Ports
After you remove any packages that are not required and disable preinstalled services that might not be removed, it is critical to set your firewall rules accordingly. If you don’t have a web server, there is no reason to allow packets to TCP ports 80 and 443.
### Avoid Legacy Protocols
Instead of Telnet, the SSH protocol is now widely available. For example, the Secure File Transfer Protocol (SFTP) protocol provides a great alternative to the TFTP protocol. The critical point is that a secure alternative is selected and used.
### Remove Identification Strings
Whenever you connect to a remote server, it usually replies with its version number. This information would reveal various information to the attacker, such as the name of the server/program, the version number, and the host operating system.

## Update and Upgrade Policies
It is vital that you keep your system updated with the latest security patches and bug fixes.
You can update a Debian-based distribution, such as Ubuntu, with the following two commands:
1. `apt update` to download package information from the configured sources
2. `apt upgrade` to install available upgrades for all packages from the configured sources
You can update a RedHat or Fedora system using the following:
- `dnf update` on newer releases (Red Hat Enterprise Linux 8 and later)
- `yum update` on older releases (Red Hat Enterprise Linux 7 and earlier)
Since we are talking about production systems, we need to select distributions that will continue to receive updates smoothly for many years.

### Ubuntu LTS Releases
For example, Ubuntu releases a Long Term Support (LTS) version every two years. LTS releases have an even version number (indicating the year) with 04 (for April), such as 18.04, 20.04, and 22.04. An LTS version will grant you five years of security updates for the base OS without a subscription and another five years if you pay for Extended Security Maintenance (ESM). For more information, you might want to check [The Ubuntu lifecycle and release cadence](https://ubuntu.com/about/release-cycle).
### RedHat Releases
RedHat Enterprise Linux 8 and 9 offer 12 years of support in three phases:
1. Full Support for five years
2. Maintenance Support for five years
3. Extended Life Phase for two years
For example, Red Hat Enterprise Linux 9 was released on May 18, 2022. It can benefit from updates as follows:
4. Full support till May 31, 2027
5. Maintenance support till May 31, 2032
For more details, check [Red Hat Enterprise Linux Life Cycle](https://access.redhat.com/support/policy/updates/errata/).

### Kernel Updates
Updating the system should not be limited to the installed software; it should consider updating the kernel. For instance, in 2016, a security vulnerability that affects the Linux kernel was discovered. It allows an attacker to gain root access to a system by exploiting a race condition in the copy-on-write (COW) mechanism, giving it the name “Dirty COW.” The vulnerability is present in all Linux kernel versions from 2.6.22 onwards. It has been patched in most major Linux distributions, but it is still a threat to systems that have not been updated.
Because Dirty COW is a severe vulnerability that can allow attackers to gain root access to Linux systems, it is crucial to keep your system, including its kernel, up-to-date with the latest security patches to reduce the risk of exploitation.

## Audit and Log
Most log files on Linux systems are stored in the **`/var/log`** directory. Here are a few of the logs that can be referenced when looking into threats:

- `/var/log/messages` - a general log for Linux systems
- `/var/log/auth.log` - a log file that lists all authentication attempts (Debian-based systems)
- `/var/log/secure` - a log file that lists all authentication attempts (Red Hat and Fedora-based systems)
- `/var/log/utmp` - an access log that contains information regarding users that are currently logged into the system
- `/var/log/wtmp` - an access log that contains information for all users that have logged in and out of the system
- `/var/log/kern.log` - a log file containing messages from the kernel
- `/var/log/boot.log` - a log file that contains start-up messages and boot information

We will keep this task short and include only two handy commands for large log files.

- Since new events are appended to the log file, you can view the last few lines using `tail`. For example, `tail -n 12 boot.log` will display the last 12 lines.
- One way to search log lines containing a specific keyword is using the command `grep`. For instance, `grep FAILED boot.log` will only show the lines with the word `FAILED`.

Note that you must be logged in as root or precede your commands with `sudo` to view the system log files.