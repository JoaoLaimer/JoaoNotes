A firewall is a system, or group of systems, that enforces an access control policy between networks.
**Common Firewall Properties**
All firewalls share some common properties:
- Firewalls are resistant to network attacks.
- Firewalls are the only transit point between internal corporate networks and external networks because all traffic flows through the firewall.
- Firewalls enforce the access control policy.
**Firewall Benefits**
There are several benefits of using a firewall in a network:
- They prevent the exposure of sensitive hosts, resources, and applications to untrusted users.
- They sanitize protocol flow, which prevents the exploitation of protocol flaws.
- They block malicious data from servers and clients.
- They reduce security management complexity by off-loading most of the network access control to a few firewalls in the network.
**Firewall Limitations**
Firewalls also have some limitations:
- A misconfigured firewall can have serious consequences for the network, such as becoming a single point of failure.
- The data from many applications cannot be passed over firewalls securely.
- Users might proactively search for ways around the firewall to receive blocked material, which exposes the network to potential attack.
- Network performance can slow down.
- Unauthorized traffic can be tunneled or hidden as legitimate traffic through the firewall.
## Firewall Architectures
### Private And Public
The public network (or outside network) is untrusted, and the private network (or inside network) is trusted.
Typically, a firewall with two interfaces is configured as follows:
- Traffic originating from the private network is permitted and inspected as it travels toweard the public network. Inspected traffic returning from the public network and associated with traffic that originated from the private network is permitted.
- Traffic originating from the public network and traveling to the private network is generally blocked.
### Demilitarized Zone
Or DMZ is a firewall design where there is typically one inside interface connected to the private network, one outside interface connected to the public network, and one DMZ interface.
- Traffic originating from the private network is inspected as it travels towards the public or DMZ network. Inspected traffic returning from the private and DMZ network is permitted.
- Traffic originating from the DMZ network and travelling to the private network is usually blocked.
- Traffic originating from the DMZ network and traveling to the public network is selectively permitted and inspected. Return traffic from the DMZ to the public network is dynamically permitted.
- Traffic originating from the public network and traveling to the private network is blocked.
### Zone-Based Policy Firewalls
Or ZPFs use the concept of zones to provide additional flexibility. By default, the traffic between interfaces in the same zone is not subject to any policy and passes freely. However, all zone-to-zone traffic is blocked. In order to permit traffic between zones, a policy allowing or inspecting traffic must be configured.
The only exception to this default **deny any** policy is the router self zone. The self zone is the router itself and includes all the router interface IP addresses.

# Firewall Types
### Packet Filtering (Stateless) Firewall
Packet filtering firewalls are usually part of a router firewall, which permits or denies traffic based on Layer 3 or Layer 4 information. They are stateless firewalls that use a simple policy table look-up that filters traffic based on specific criteria.
### Stateful Firewall
Are the most versatile and most common firewall technologies in use. Stateful firewalls provide stateful packet filtering by using connection information maintained in a state table. Stateful filtering is a firewall architecture that is classified at the network layer. It also analyzes traffic at OSI Layer 4 and Layer 5.
### Application Gateway Firewall
An application gateway firewall (proxy firewall), filters information at Layers 3, 4, 5 and 7. Most of the firewall control and filtering is done in software. When a client access a remote server, it connects to a proxy server. the proxy server connects to the remote server on behalf of the client. Therefore, the server only sees a connection from the proxy server.
### Next Generation Firewalls
Next-generation firewalls (NGFW) go beyond stateful firewalls by providing:
- Integrated intrusion prevention.
- Application awareness and control to see and block risky apps.
- Upgrade paths to include future information feeds.
- Techniques to address evolving security threats.

Other methods of implementing firewalls include:
- **Host-based (server and personal) firewall -** A PC or server with firewall software running on it.
- **Transparent firewall -** Filters IP traffic between a pair of bridged interfaces.
- **Hybrid firewall -** A combination of the various firewall types. For example, an application inspection firewall combines a stateful firewall with an application gateway firewall.