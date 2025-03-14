The Sysinternals tools is a compilation of over 70+ [[WIndows]]-based tools. Each of the tools falls into one of the following categories:
- File and Disk Utilities
- Networking Utilities
- Process Utilities
- Security Utilities
- System Information
- Miscellaneous 
[https://docs.microsoft.com/en-us/sysinternals/downloads/](https://docs.microsoft.com/en-us/sysinternals/downloads/)
You can use Sysinternals online by using the WebDAV client and attaching a the network share to your computer.

**File and Disk Utilities**:

**Sigcheck**
**Sigcheck** is a command-line utility that shows file version number, timestamp info, and digital signature details, including certificate chains. It also can check a file's status on VirusTotal.

*Use Case*: Check for unsigned files in C:\Windows\System32
*Command*: `sigcheck -u -e C:\Windows\System32`
*Parameter usage*: 
- `-u` "If VirusTotal check is enabled, show files that are unknown by VirusTotal or have non-zero detection, otherwise show only unsigned files."
- `-u` "Scan executable images only (regardless of their extension)"

**Streams**
The NTFS file system provides applications the ability to create alternate data streams of information. By using the syntax 'file:stream', you are able to read and write to alternates.
Alternate Data Streams (ADS) is a file attribute specific to Windows NTFS (New Technology File System). Every file has at least one data stream ($DATA) and ADS allows files to contain more than one stream of data. Malware writers have used ADS to hide data in an endpoint.

*Usage*:`streams <file>`

**SDelete**
**SDelete** (Secure Delete) allows you to delete one or more files and/or directories, or to cleanse the free spaces on a logical disk. SDelete implemented the DOD 5220.22-M (Department of Defense clearing and sanitizing protocol).
*DoD 5220.22-M Wipe Method*
- Pass 1: Writes a zero an verifies the write.
- Pass 2: Writes a one and verifies the write.
- Pass 3: Writes a random character and verifies the write
Source: [https://www.lifewire.com/dod-5220-22-m-2625856](https://www.lifewire.com/dod-5220-22-m-2625856)
SDelete has been used by adversaries and is associated with MITRE techniques [T1485](https://attack.mitre.org/techniques/T1485/) (**Data Destruction**) and [T1070.004](https://attack.mitre.org/techniques/T1070/004/) (**Indicator Removal on Host: File Deletion**). It's MITRE ID [S0195](https://attack.mitre.org/software/S0195/).

**Networking Utilities**

**TCPView**
**TCPView** show detailed listings of all TCP and UDP endpoints in your system.
*Usage*:`tcpview`

**Process Utilities**

**Autoruns**
**Autoruns** shows auto-starting locations, what programs are configured to run during system bootup or logins.
*Usage:* `autoruns`

**ProcDump**
**ProcDump** primary purpose is monitoring an application for CPU spikes and generating crash dumps during a spike.
*Usage*:`procdump`

**Process Explorer**
**Process Explorer** display a list of currently active processes and information about the process.
*Usage*:`procexp`

**Process Monitor**
**Process Monitor** is an advanced monitoring tool for Windows that shows real-time file system, Registry and process/thread activity.
*Usage*:`procmon`

**PsExec**
**PsExec** is a light-weight telnet-replacement that lets you execute processes on other systems, complete with full interactivity for console applications, without having to manually install client software.
PsExec is another tool that is utilized by adversaries. This tool is associated with MITRE techniques [T1570](https://attack.mitre.org/techniques/T1570) (**Lateral Tool Transfer**), [T1021.002](https://attack.mitre.org/techniques/T1021/002) (**Remote Services: SMB/Windows Admin Shares**), and [T1569.002](https://attack.mitre.org/techniques/T1569/002) (**System Services: Service Execution**). It's MITRE ID is [S0029](https://attack.mitre.org/software/S0029/).
*Usage*:`psexec`

**Security Utilities**
**[[Sysmon]]**
**Sysmon** is a Windows system service and device driver that, remains resident across system reboots to monitor and log system activity to the Windows event log.

**System Information**
**WInObj**
**WinObj** is a 32-bit Windows NT Program that uses the native Windows NT API to access and display info on the NT Object Manager's name space.
Session 0 is the OS session.
Session 1 is the User session.
*Usage*:`winobj`

**Miscellaneous**
**BgInfo**
BgInfo display relevant info about a Windows computer.

**RegJump**
**RegJump** takes a registry path and makes Regedit open to that path.
*Usage*:`regjump <path>`

**Strings** 
**Strings** scans file you pass it for UNICODE (or ASCII) strings of a default length of 3 or more UNICODE (or ASCII) characters.
*Usage*:`strings <path>`

**Real-world scenario**: As a security engineer, I had to work with vendors to troubleshoot why an agent wasn't responding on an endpoint—the tools used were **ProcExp**, **ProcMon**, and **ProcDump**.

- ProcExp = to inspect the agent process, its properties, and associated threads and handles.
- ProcMon = to investigate if there were any indicators on why the agent was not operating as it should.
- ProcDump = to create a dump of the agent process to send to the vendor for further analysis.