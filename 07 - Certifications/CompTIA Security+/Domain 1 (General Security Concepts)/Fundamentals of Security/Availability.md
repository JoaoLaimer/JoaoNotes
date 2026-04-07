Used to ensure that information, systems, and resources are accessible and operational when needed by authorized users.

99.9% Availability (3 Nines): In a year a system can be down for a maximum of 8.76 hours.

99.999% Availability (5 Nines): In a year a system can be down for a maximum of 5.26 minutes.

99% Uptime: downtime of 3.5 days per year.

- Ensuring Business Continuity. 
- Maintaining Customer Trust.
- Upholding and Organization's Reputation.

# How to achieve Availability
## Redundancy
Duplication of critical components or functions of a system with the intention of enhancing its reliability, provides fault tolerance. Aims to remove every **single point of failure (SPOF)**.
#### Disk Redundancy
Fault-tolerant disks, such RAID-1 (mirroring), RAID-5 (striping with parity), and RAID-10 (striping with mirror), allows a system to continue to operate even if a disk fails.
#### Server Redundancy
Involves using multiple servers in a load balance so that if one is overloaded or fails, the other servers can take over the load to continue supporting end users.
#### Data Redundancy
Involves storing data in multiple places
#### Network Redundancy
Ensures that if one network path fails, the data can travel through another route. Can be achieved using NIC teaming, putting two o more network cards in a single server.
#### Power Redundancy
Involves using backup power sources to ensure that an organization's system remain operational during periods of power disruption or outages within a local service area. Achieved using UPS (Uninterruptible power supplies).

# AVAILABILITY <-> REDUNDANCY
