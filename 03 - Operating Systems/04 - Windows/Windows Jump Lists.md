
[[Windows]] introduced jump lists to help users go directly to their recently used files from the taskbar. We can view jumplists by right-clicking an application's icon in the taskbar, and it will show us the recently opened files in that application. stored in the following directory:

`C:\Users\<username>\AppData\Roaming\Microsoft\Windows\Recent\AutomaticDestinations`

We can use Eric Zimmerman's JLECmd.exe to parse Jump Lists. We can use the following command to parse Jumplists using JLECmd.exe:

`JLECmd.exe -f <path-to-Jumplist-file> --csv <path-to-save-csv>`