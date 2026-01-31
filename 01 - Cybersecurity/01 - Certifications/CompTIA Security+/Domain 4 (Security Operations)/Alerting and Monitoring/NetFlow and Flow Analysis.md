## Full Packet Capture (FPC)
Captures the entire packet, including the header an the payload for all traffic entering and leaving a network.
## Flow Analysis
Relies on a flow collector, which records metadata and statistics rather than recording each frame that passes through the network
Flow analysis does not provide the actual content.
Flow analysis rapidly generate visualization to map network connections, traffic types, and session volumes.
## NetFlow 
A Cisco-developed means of reporting network flow info to a structured database.
> NetFlow can interpret traffic flow, but it is up to the analyst to interpret the data and identify a type of network attack.
## IP Flow Information Export (IPFIX)
Defines traffic flows based on shared packets characteristics
- Protocol Interface
- IP Version/Type
- Source/Destination IP
- Source/Destination port
- IP service type
## Zeek
Passively monitors a network like a sniffer, but only logs full packet capture data of potential interest.
Performs normalization of the data and stores it as a tab-delimited or JSON-formatted text file.
## Multi Router Traffic Grapher (MRTG)
Creates graphs showing traffic flows through the network interfaces of routers and switches by polling the appliances using SNMP.