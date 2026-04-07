Use digital forensic collection techniques to make forensic images of the data on those servers.

Capture and hash the system images.
Capture screenshots of the machine.
Always follow the order of volatility when collecting evidence.
Review licensing and documentation for all systems.
## Data Acquisition
The method and tools used to create a forensically sound copy of the data from a source device, such as system memory or a hard disk.
Policies for bringing one's own device (BYOD) complicate data acquisition because it may not be legally possible to search or seize the devices.

Some data can only be collected once the system is shutdown or the power is suddenly disconnected.
1. CPU registers and cache memory
2. System memory (RAM), routing tables, ARP caches, process table, temporary swap files.
3. Data on persistent mass storage (HDD/SDD/flash drive)
4. Remote logging and monitoring data.
5. Physical configuration and network topology
6. Archival Media
#### WARNING
Some Windows registry keys,like HKLM/Hardware, are only in memory and require a memory dump to analyze.
