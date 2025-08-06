# Registry Entries  - [[Windows]]
# System Information and System Accounts
**Os Version** : `SOFTWARE\Microsoft\Windows NT\CurrentVersion`
**Computer Name:** `SYSTEM\CurrentControlSet\Control\ComputerName\ComputerName`
**Time Zone Information:** `SYSTEM\CurrentControlSet\Control\TimeZoneInformation`
**Network Interfaces and Past Networks:** `SYSTEM\CurrentControlSet\Services\Tcpip\Parameters\Interfaces` `SOFTWARE\Microsoft\Windows NT\CurrentVersion\NetworkList\Signatures\Unmanaged`
`SOFTWARE\Microsoft\Windows NT\CurrentVersion\NetworkList\Signatures\Managed`
**Autostart Programs (Autoruns):** `NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Run`
`NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\RunOnce`
`SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce`
`SOFTWARE\Microsoft\Windows\CurrentVersion\policies\Explorer\Run`
`SOFTWARE\Microsoft\Windows\CurrentVersion\Run`

**SAM hive and user information:** `SAM\Domains\Account\Users`
# Registry Entries - Usage of files/folders

**Recent Files**: `NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs`

**Office Recent FIles:** `NTUSER.DAT\Software\Microsoft\Office\VERSION`

**ShellBags**: When any user opens a folder, it opens in a specific layout. Users can change this layout according to their preferences. These layouts can be different for different folders. This information about the Windows _'shell'_ is stored and can identify the Most Recently Used files and folders. Since this setting is different for each user, it is located in the user hives. 
`USRCLASS.DAT\Local Settings\Software\Microsoft\Windows\Shell\Bags`
`USRCLASS.DAT\Local Settings\Software\Microsoft\Windows\Shell\BagMRU`
`NTUSER.DAT\Software\Microsoft\Windows\Shell\BagMRU`
`NTUSER.DAT\Software\Microsoft\Windows\Shell\Bags`

**Windows Explorer Address/Search Bars:** : `NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\TypedPaths`
`NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\WordWheelQuery`

**Open/Save and LastVisited Dialog MRUs:** `NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\ComDlg32\OpenSavePIDlMRU`
`NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\ComDlg32\LastVisitedPidlMRU`

# Registry Entries - Evidence of Execution
**UserAssist**: `NTUSER.DAT\Software\Microsoft\Windows\Currentversion\Explorer\UserAssist\{GUID}\Count`
**ShimCache:** `SYSTEM\CurrentControlSet\Control\Session Manager\AppCompatCache`
**AmCache:** `C:\Windows\appcompat\Programs\Amcache.hve`
`Amcache.hve\Root\File\{Volume GUID}\`
**BAM/DAM**: `SYSTEM\CurrentControlSet\Services\bam\UserSettings\{SID}`
`SYSTEM\CurrentControlSet\Services\dam\UserSettings\{SID}`

# External Devices / USB device

**Device identification:** `SYSTEM\CurrentControlSet\Enum\USBSTOR`
`SYSTEM\CurrentControlSet\Enum\USB`
**First/Last Times:** `SYSTEM\CurrentControlSet\Enum\USBSTOR\Ven_Prod_Version\USBSerial#\Properties\{83da6326-97a6-4088-9453-a19231573b29}\####`
**USB device Volume Name:** `SOFTWARE\Microsoft\Windows Portable Devices\Devices`