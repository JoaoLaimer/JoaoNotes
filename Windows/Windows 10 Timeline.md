
[[Windows]] 10 stores recently used application and files in an SQLite database called the Windows 10 Timeline.

The Windows 10 timeline can be found at the following location:

`C:\Users\<username>\AppData\Local\ConnectedDevicesPlatform\{randomfolder}\ActivitiesCache.db`

We can use Eric Zimmerman's WxTCmd.exe for parsing Windows 10 Timeline. We can use the following command to run WxTCmd:

`WxTCmd.exe -f <path-to-timeline-file> --csv <path-to-save-csv>`