Common weaknesses:
- Misconfigurations on Windows services or scheduled tasks.
- Excessive privileges assigned to out account.
- Vulnerable software.
- Missing Windows security patches.

**Windows Users**
- **Administrators**: These users have the most privileges. 
- **Standard Users**: Can perform limited tasks.
Any user with administrative privileges will be part of the **Administrators** group. Standard users are part of the **Users** group.

There are, also, special built-in accounts used by the operating system:
- **System / LocalSystem**: Used by the OS to perform internal tasks. It has access to all files and resources available on the host with even higher privileges than administrators.
- **Local Service**: Default account used to run Windows services with "minimum" privileges. It will use anonymous connections over the network.
- **Network Service**: Used to run services with "minimum" privileges. It will use the computer credentials to authenticate through the network.


# Unattended Windows Installation
When installing Windows on a large number of hosts, the administrators may use Windows Deployment Services, which allows for a single operating system image to be deployed to several hosts through the network. These installations are called Unattended Installations. Such installations require the use of an administrator account to perform the initial setup, which might end up being stored in the machine in the following locations: 
- C:\Unattend.xml
- C:\Windows\Panther\Unattend.xml
- C:\Windows\Panther\Unattend\Unattend.xml
- C:\Windows\system32\sysprep.inf
- C:\Windows\system32\sysprep\sysprep.xml
# Powershell History

If a user runs a command that includes a password directly as part of the Powershell command line, it can be retrieved by using the following command from a cmd.exe prompt:
``type %userprofile%\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadline\ConsoleHost_history.txt``

**Note:** The command above will only work from cmd.exe, as Powershell won't recognize `%userprofile%` as an environment variable. To read the file from Powershell, you'd have to replace `%userprofile%` with `$Env:userprofile`.

# Saved Windows Credentials 

Windows allows us to use other users' credentials. This function also gives the option to save these credentials on the system.
```shell-session
cmdkey /list
```

While you can't see the actual passwords, if you notice any credentials worth trying, you can use them with the `runas` command and the `/savecred` option, as seen below.

```shell-session
runas /savecred /user:admin cmd.exe
```

# IIS Configuration

internet Information Services (IIS) is the default web server on Windows installations. The configuration of websites on IIS is stored in a file called web.config and can store passwords for databases or configured authentication mechanisms. We can find `web.config` in one of the following locations:

- C:\inetpub\wwwroot\web.config
- C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\web.config

Here is a quick way to find database connection strings on the file:

```shell-session
type C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\web.config | findstr connectionString
```
# Retrieve Credentials from Software


**PuTTY**

To retrieve the stored proxy credentials, tou can search under the following registry key for ProxyPassword with the following command:

```shell-session
reg query HKEY_CURRENT_USER\Software\SimonTatham\PuTTY\Sessions\ /f "Proxy" /s
```

**Note:** Simon Tatham is the creator of PuTTY (and his name is part of the path), not the username for which we are retrieving the password. The stored proxy username should also be visible after running the command above.

Just as putty stores credentials, any software that stores passwords, including browsers, email clients, FTP clients, SSH clients, VNC software and others, will have methods to recover any passwords the user has saved.

# Scheduled Tasks

Scheduled tasks can be listed from the command line using the `schtasks` command without any options. To retrieve detailed information about any of the services, you can use a command like the following one:

```shell-session
schtasks /query /tn vulntask /fo list /v
```

If our current user can modify or overwrite the "Task to Run" executable, we can control what gets executed by the taskusr1 user, resulting in a simple privilege escalation. To check the file permissions on the executable, we use `icacls`
