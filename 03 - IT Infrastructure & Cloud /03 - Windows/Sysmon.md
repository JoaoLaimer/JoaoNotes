System Monitor is a [[Windows]] system service and device driver that remains resident across system reboots to monitor and log system activity. Communly used in conjuction with [[SIEM]]s.

Events are stored in 
`Applications and Services Logs/Microsoft/Windows/Sysmon/Operational`

**Sysmon Config File**
Sysmon requires a config file to determine how it analyses the events that it receives.
SwiftOnSecurity Sysmon config file: [Sysmon-Config.](https://github.com/SwiftOnSecurity/sysmon-config)

**Installing Sysmon** 
PowerShell command: `Download-SysInternalsTools C:\Sysinternals`

**Sysmon "Best Practices"**
- Prioritize excluding events.
- CLI gives you further control.
Event ID 1: Process Creation
Event ID 3: Network Connection
Event ID 7: Image Loaded
Event ID 8: CreateRemoteThread
Event ID 11: File Created
Event ID 12 / 13 / 14: Registry Event
Event ID 15: FileCreateStreamHash
