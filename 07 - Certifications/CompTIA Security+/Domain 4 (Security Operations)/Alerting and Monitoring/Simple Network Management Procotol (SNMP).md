Internet protocol for collecting and organizing information about managed devices on IP networks and for modifying that information to change device behavior.
Devices:
- Routers
- Switches
- Firewalls
- Printers
- Server
- End User Client Devices
## Management Information Base (MIB)
Use to describe the structure of the management data of a device subsystem using a hierarchical namespace containing object identifiers.
## Verbose 
SNMP traps may be configured to contain all the information about a giver alert or event as a payload.
Data in these SNMP traps are stored in a simple key-value pair configuration known as a "variable binding"

SNMP Version one and two use a community string to give them access to the device as their security mechanism.
Default community strings of public (read-only) or private (read-write) devices are considered a security risk.

SNMP Version 3 provides three security enhancements which added integrity, authentication, and confidentiality to the SNMP protocol.

Since DES is considered a weak algorithm, it is being replaced with 3DES and AES in newer devices that reply on SNMPv3

> Administrators use SNMPv3 to manage and monitor network devices, and SNMP uses UDP ports 161 and 162. SNMPv3 encrypts credentials before sending them over the network and is more secure than earlier versions.


