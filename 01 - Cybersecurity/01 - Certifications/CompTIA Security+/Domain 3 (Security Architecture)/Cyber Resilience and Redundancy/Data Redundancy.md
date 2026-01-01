## Redundant Array of Independent Disks (RAID)
Combines multiple physical storage devices into a recognized single logical storage device.
### RAID 0
Provides data striping across multiple disks to increase performance
**Striping**: Data is split across multiple drives, so access is parallel. 

RAID 0 is for performance without fault tolerance concerns.
### RAID 1
Mirrors data for redundancy across two drives.
**Mirroring**

Complete data mirroring, but, less space. The complete capacity is equal to the smaller disk.
### RAID 5
Stripes data with parity, using at least three storage devices.
**Striping with parity**

They calculate missing data on a drive.
### RAID 6
Uses data striping across multiple devices with two pieces of parity data.
**Striping with double parity**
### RAID 10
Combines RAID 1 and RAID 0, featuring mirrored arrays in a striped setup.
**Striped array of mirrored arrays**
At least 4 drives, and has to have even number of disks.

## Failure-resistant
Use of redundant storage to withstand hardware malfunctions without data loss.
Failure-resistant systems include RAID 1 and RAID 10, using mirroring for data redundancy.
## Fault-tolerant
Use of RAID 1,5,6 and 10 for uninterrupted operation during hardware failures.
## Disaster-tolerant
Protects data from catastrophic entes.
RAID 1 and RAID 10.