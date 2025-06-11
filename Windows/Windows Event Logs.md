Ge**Event Viewer**
[[Windows]] Event Logs are not text files that can be viewed using a text editor. However, the raw data can be translated into [[XML]] using the Windows API.
Logs with the .evtx file extension reside in C:\Windows\System32\winevt\Logs.

**Elements of Windows Event Log**
- System Logs: Records events associated with the Operating System segments.
- Security Logs: Records events connected to logon and logoff.
- Application Logs: Records events related to applications installed on a system.
- Directory Service Events: [[Active Directory]] changes and activities recorded in these logs, mainly domain controllers.
- File Replication Service Events: Records events associated with Windows Servers during the sharing of Group Policies and logon scripts to domain controllers, from where they may be accessed by the users through the client servers.
- DNS Event Logs: DNS servers use these logs to record domain events and to map out.
- Custom Logs: Events are logged by application that require custom data storage.

There are three main ways of accessing these event logs within a Windows system:
1. **Event Viewer** (GUI-based application)
2. **Wevtutil.exe** (command-line tool)
3. **Get-WinEvent** (PowerShell cmdlet)

Event Viewer, a Microsoft Management Console (MMC) snap-in, can be launched by selecting Event Viewer in the taskbar, or typing `eventvwr.msc`.

**wevtutil.exe**

wevtutil.exe allow you to query events logs via the command line and/or [[PowerShell]].
To learn more about a specific command, type the following:
`wevtutil COMMAND /?`

**Get-WinEvent**
It provides information on event logs and event log providers. Additionally, you can combine numerous events from multiple sources into a single command and filter using XPath queries, structured XML queries, and hash table queries.

**XPath Queries**

XPath or XMP Path Language.

Below is an example XPath query along with its explanation:

The following query selects all events from the channel or log file where the severity level is less than or equal to 3 and the event occurred in the last 24 hour period. 
```
XPath Query: *[System[(Level <= 3) and TimeCreated[timediff(@SystemTime) <= 86400000]]]
```
an XPath event query starts with '`*`' or '**Event**'.
Note that both wevtutil and Get-WinEvent support XPath queries as event filters.

**Event IDs**

https://static1.squarespace.com/static/552092d5e4b0661088167e5c/t/580595db9f745688bc7477f6/1476761074992/Windows+Logging+Cheat+Sheet_ver_Oct_2016.pdf

https://web.archive.org/web/20190115215749/https://apps.nsa.gov/iaarchive/customcf/openAttachment.cfm?FilePath=/iad/library/ia-guidance/security-configuration/applications/assets/public/upload/Spotting-the-Adversary-with-Windows-Event-Log-Monitoring.pdf&WpKes=aF6woL7fQp3dJiqyJL2LenrLxuHC7ztGtVNK3x
