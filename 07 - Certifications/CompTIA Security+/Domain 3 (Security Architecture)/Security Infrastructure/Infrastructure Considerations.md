## Correct Placement of Devices
- Routers
- Switches
- Access Points
Proper placement should achieve:
- Optimal data flow
- Minimized latency
- Robust defense
Unproper placement can cause:
- Network bottlenecks
- Vulnerability points
- Areas without connectivity
## Security Zone
- **Intranet**: Is an internal network. People use the intranet to communicate and share content with each other. While it's common for an intranet to include internal web servers, this isn't a requirement.
- **Extranet**: is a part of a network that can be accessed by authorized entities from outside of the network.
Distinct segment within a network often created by logically isolating the segment using a firewall or other security device.
- Public-facing services
- Internal employee resources
- Sensitive data storage
Remember the term screened subnet
## Screened Subnet
Hosts public-facing services such as web servers, email servers, and DNS servers and safeguards against security breaches by preventing attackers from gaining direct access to the sensitive core internal network.
>Sometimes called a DMZ (Demilitarized Zone).
## Attack Surface of a Network
Refers to all the points where an unauthorized users can try to enter data or extract data from an environment.
- Improper device placement
- Improperly configured devices 
- Outdated software
- Unnecessary open ports
- Weak access controls
## Connectivity
Refers to how different components of a network communicate with each other and with other external networks.
- Wi-Fi
- Microwave Links
- Satellite Connections
Filter optics excel in speed, reliability, and signal quality for robust connectivity.
Considerations:
- Scalability
- Speed requirements
- Security considerations
- Budgetary constraints
## Devices Attributes
- Active
- Passive
**Inline**: An inline  device sits in the network traffic path, and is able to control or block traffic as it passes through this device;
- Firewall
- Router
- IPS
**Tap-Based Configuration**: Taps and monitors operate discreetly outside the network path, capturing data for analysis without impacting traffic.
- Health
- Performance
- Security
## Failure Mode
- **Fail-open**: allows all traffic in the event of a failure.
- **Fail-closed**: blocks all traffic in the event of a failure.
# Hardening Routers
- ACLs
> Broadcast storm and loop prevention such as STP (Spanning Tre Protocol) and (Rapid RSTP) RSTP is necessary to protect against switching loop problems, such as those caused when two ports of a switch are connect.

# East-west Traffic
Image looking at a network diagram of servers within a network. These usually show servers configured horizontally, so traffic between them travels east and west.
