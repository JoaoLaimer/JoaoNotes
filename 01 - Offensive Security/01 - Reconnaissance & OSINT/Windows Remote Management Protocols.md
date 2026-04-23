Remote management is enabled by default starting with Windows Server 2016. Remote management is a component of the Windows hardware management features that manage server hardware locally and remotely.
The main components used for remote management of Windows and Windows servers are the following:

- Remote Desktop Protocol (`RDP`)
- Windows Remote Management (`WinRM`)
- Windows Management Instrumentation (`WMI`)
# RDP
The [Remote Desktop Protocol](https://docs.microsoft.com/en-us/troubleshoot/windows-server/remote/understanding-remote-desktop-protocol) (`RDP`) is a protocol developed by Microsoft for remote access to a computer running the Windows operating system. This protocol allows display and control commands to be transmitted via the GUI encrypted over IP networks. RDP works at the application layer in the TCP/IP reference model, typically utilizing TCP port 3389 as the transport protocol. However, the connectionless UDP protocol can use port 3389 also for remote administration.
RDP has handled [Transport Layer Security](https://en.wikipedia.org/wiki/Transport_Layer_Security) (`TLS/SSL`) since Windows Vista, which means that all data, and especially the login process, is protected in the network by its good encryption.
## Footprinting the Service
Scanning the RDP service can quickly give us a lot of information about the host. For example, we can determine if `NLA` is enabled on the server or not, the product version, and the hostname.
```
$ nmap -sV -sC 10.129.201.248 -p3389 --script rdp*
```
In addition, we can use `--packet-trace` to track the individual packages and inspect their contents manually. We can see that the `RDP cookies` (`mstshash=nmap`) used by Nmap to interact with the RDP server can be identified by `threat hunters` and various security services such as [Endpoint Detection and Response](https://en.wikipedia.org/wiki/Endpoint_detection_and_response) (`EDR`), and can lock us out as penetration testers on hardened networks.
#### RDP Security Check
```
$ git clone https://github.com/CiscoCXSecurity/rdp-sec-check.git && cd rdp-sec-check

$ ./rdp-sec-check.pl 10.129.201.248
```
Authentication and connection to such RDP servers can be made in several ways. For example, we can connect to RDP servers on Linux using `xfreerdp`, `rdesktop`, or `Remmina` and interact with the GUI of the server accordingly.
#### Initiate an RDP Session
```
$ xfreerdp /u:cry0l1t3 /p:"P455w0rd!" /v:10.129.201.248
```

# WinRM
The Windows Remote Management (`WinRM`) is a simple Windows integrated remote management protocol based on the command line. WinRM uses the Simple Object Access Protocol (`SOAP`) to establish connections to remote hosts and their applications. Therefore, WinRM must be explicitly enabled and configured starting with Windows 10. WinRM relies on `TCP` ports `5985` and `5986` for communication, with the last port `5986 using HTTPS`, as ports 80 and 443 were previously used for this task. However, since port 80 was mainly blocked for security reasons, the newer ports 5985 and 5986 are used today.
## Footprinting the Service
WinRM uses TCP ports `5985` (`HTTP`) and `5986` (`HTTPS`) by default, which we can scan using Nmap. However, often we will see that only HTTP (`TCP 5985`) is used instead of HTTPS (`TCP 5986`).
#### Nmap WinRM
```
$ nmap -sV -sC 10.129.201.248 -p5985,5986 --disable-arp-ping -n
```
If we want to find out whether one or more remote servers can be reached via WinRM, we can easily do this with the help of PowerShell. The [Test-WsMan](https://docs.microsoft.com/en-us/powershell/module/microsoft.wsman.management/test-wsman?view=powershell-7.2) cmdlet is responsible for this, and the host's name in question is passed to it. In Linux-based environments, we can use the tool called [evil-winrm](https://github.com/Hackplayers/evil-winrm), another penetration testing tool designed to interact with WinRM.
```
$ evil-winrm -i 10.129.201.248 -u Cry0l1t3 -p P455w0rD!
```
## WMI
Windows Management Instrumentation (`WMI`) is Microsoft's implementation and also an extension of the Common Information Model (`CIM`), core functionality of the standardized Web-Based Enterprise Management (`WBEM`) for the Windows platform. WMI allows read and write access to almost all settings on Windows systems. Understandably, this makes it the most critical interface in the Windows environment for the administration and remote maintenance of Windows computers, regardless of whether they are PCs or servers. WMI is typically accessed via PowerShell, VBScript, or the Windows Management Instrumentation Console (`WMIC`). WMI is not a single program but consists of several programs and various databases, also known as repositories.
## Footprinting the Service
The initialization of the WMI communication always takes place on `TCP` port `135`, and after the successful establishment of the connection, the communication is moved to a random port.
#### WMIexec.py
```
$ /usr/share/doc/python3-impacket/examples/wmiexec.py Cry0l1t3:"P455w0rD!"@10.129.201.248 "hostname"
```