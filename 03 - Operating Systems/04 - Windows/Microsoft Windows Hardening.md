# General Concepts
### Services  
Windows Services create and manage critical functions such as network connectivity, storage, memory, sound, user credentials, and data backup and runs automatically in the background. These services are divided into three categories, i.e. Local, Network & System. 
Type `services.msc` in the Run window to access Windows services.

### Windows Registry
The Windows registry is a unified container database that stores configurational settings, essential keys and shared preferences for Windows and third-party applications.
Type `regedit` in the Run dialogue or taskbar search to access the registry editor.

### Event Viewer
Event Viewer is an app that shows log details about all events occurring on your computer, including driver updates, hardware failures, changes in the operating system, invalid authentication attempts and application crash logs.
Event categories are as below:
- **Application:** Records events of already installed programs.
- **System:** Records events of system components.
- **Security:** Logs events related to security and authentication etc.
We can access Event Viewer by typing `eventvwr` in the Run window.

### Telemetry
Telemetry is a data collection system used by Microsoft to enhance the user experience by preemptively identifying security and functional issues in software. Telemetry functionality is achieved by Universal Telemetry Client (UTC) services available in Windows and runs through `diagtrack.dll`. Contents acquired through telemetry service are stored encrypted in a local folder `%ProgramData%\Microsoft\Diagnosis` and sent to Microsoft after 15 minutes or so.
We can access `The DiagTrack` through the Services console in Windows 10.

# Identity & Access Management
## Standard vs Admin Account
Identity and access management involves employing best practices to ensure that only authenticated and authorized users can access the system. There are two types of accounts in Windows, i.e. Admin and Standard Account. Per best practice, the Admin account should only be used to carry out tasks like software installation and accessing the registry editor, service panel, etc.
Go to `Control Panel > User Accounts` to create standard or administrator accounts.

## User Account Control (UAC)
User Account Control (UAC) is a feature that enforces enhanced access control and ensures that all services and applications execute in non-administrator accounts. It helps mitigate malware's impact and minimises privilege escalation by [bypassing UAC](https://tryhackme.com/room/bypassinguac). Actions requiring elevated privileges will automatically prompt for administrative user account credentials if the logged-in user does not already possess these. To access UAC, go to `Control Panel -> User Accounts` and click on `Change User Account Control Setting`.

## Local Policy and Group Policies Editor
Group Policy Editor is a built-in interactive tool by Microsoft that allows to configure and implement local and group policies. We mainly use this feature when part of a network; however, we can also use it for a workstation to limit the execution of vulnerable extensions, set password policies, and other administrative settings.
**Note**: The feature is not available in Windows Home but only in the Pro and Enterprise versions.
### Password Policies
One primary use of a local policy editor is to ensure complex and strong passwords for user accounts. We can access Password policies through the Local group policy editor.
Go to `Security settings > Account Policies > Password policy`
### Setting A Lockout Policy
To protect your system password from being guessed by an attacker, we can set out a lockout policy so the account will automatically lock after certain invalid attempts. To set a lockout policy, go to `Local Security Policy > Windows Settings > Account Policies > Account Lockout Policy` and configure values to lock out hackers after three invalid attempts.

# Network Management
## Windows Defender Firewall
We can access Windows Defender Firewall by accessing `WF.msc` in the Run dialogue.
It has three main profiles `Domain, Public and Private`The Private profile must be activated with "Blocked Incoming Connections" while using the computer at home. 
View detailed settings for each profile by clicking on Windows Defender Firewall Properties.
Whenever possible, enable the Windows Defender Firewall default settings. For blocking all the incoming traffic, always configure the firewall with a 'default deny' rule before making an exception rule that allows more specific traffic.
## Disable unused Networking Devices
If the device is improperly configured or not being used by the owner, it is recommended to disable the interface so that threat actors cannot access them and use them for data retrieval from the victim's computer.  

To disable the unused Networking Devices, go to the `Control panel > System and Security Setting > System > Device Manager` and disable all the unused Networking devices.
## **Disable SMB protocol**

SMB is a file-sharing protocol exploited by hackers in the wild. The protocol is primarily used for file sharing in a network; therefore, you must disable the protocol if your computer is not part of a network by issuing the [following](https://docs.microsoft.com/en-us/windows-server/storage/file-server/troubleshoot/detect-enable-and-disable-smbv1-v2-v3) command in PowerShell.

```PowerShell
user@machine$ Disable-WindowsOptionalFeature -Online -FeatureName SMB1Protocol Path          :
Online        : True 
RestartNeeded : False
```
## Protecting Local Domain Name System (DNS)
The hosts file located in Windows acts like local DNS and is responsible for resolving hostnames to IP addresses. Malicious actors try to edit the file's content to reroute traffic to their command and control server.  
The hosts file is located at `C:\Windows\System32\Drivers\etc\hosts`.

## Mitigating Address Resolution Protocol Attack
You can check ARP entries using the command **`arp -a`** in the command prompt. The table contains MAC addresses in the middle and IP addresses in the left.  If the table includes a MAC mapped to two IPs, you are probably susceptible to an ARP poisoning attack.
To clear the ARP cache and prevent the attack, issue the command `arp -d`.
## Preventing Remote Access to Machine
We must disable remote access (if not required) by going to `settings > Remote Desktop`.