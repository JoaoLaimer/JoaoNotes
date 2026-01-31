Safeguard networks by monitoring and controlling traffic based on predefined security rules
Firewalls can be hardware appliances or specialized software installed on a device to control network traffic.
## Screened Subnet (Dual-homed Host)
Acts as a security barrier between external untrusted networks and internal trusted networks, using a protected host with security measures like a packet-filtering firewall.
Install a firewall in a network to set up a screened subnet.

A firewall with in-depth inspection may slow down the device due to the time taken for each packet to pass through all the rules
## Packet Filtering Firewall (Layer 4) (Stateless)
Checks packet headers for traffic allowance based on IP addresses and port numbers.
Cannot prevent certain attacks due to limited inspection capabilities in the packet header.
## Stateful Firewall 
Monitors all inbound and outbound network connections and requests. Keeps tracks of conversations.
## Proxy Firewall
Acts as an intermediary between internal and external connections, making connection on behalf of other endpoints.
- **Circuit Level**: Like a SOCKS firewall, operates at the Layer 5 of the OSI model.
- **Application Level** (Layer 7): Conducts various proxy functions for each type of application at the Layer 7 of the OSI model.
## Kernel Proxy Firewall (Fifth Generation Firewall)
Has minimal impact on network performance while thoroughly inspecting packets across all layers.
## Next Generation Firewall (NGFW)
Aims to address the limitations of traditional firewalls by being more aware of application and their behaviors.
- Conducts deep packet inspection for traffic.
- Operates fast with minimal network performance impact.
- Offers full-stack traffic visibility.
- Integrates with various security products.
- Application awareness.
- User identity tracking
Organization become reliant on a single vendor due to firewall configurations tailored to their product line.

## Unified Threat Management Firewall (UTM)
Provides the ability to conduct multiple security functions in a single appliance.
- Network firewalls
- Network intrusion prevention systems
- Gateway antivirus and antispam.
- Virtual private network concentration
- Content filtering
- Load balancing
- Data loss prevention
UTM devices are a single point of failure.
- Lower upfront costs, maintenance, and power consumption.
- Simplified installation and configuration
- Full integration with multiple benefits
UTM lacks the depth of specialized tools and occasionally exhibits less efficient performance.
## Web Application Firewall (WAF)
Focuses on the inspection of the HTTP traffic.
WAF can function as standalone appliances or as software integrated into web servers.
**Inline Configuration**
Devices sits between the network firewall an the web servers.
**Out-of-Band Configuration**
Device receives a mirrored copy of web server traffic.