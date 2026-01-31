Common security feature found on network switches that allows administrators to restrict which devices can connect to a specific port based on the network interface card's  MAC address.
Switches use intelligence to prevent collisions on networks.
Switches are more efficient and secure than hubs.

Port security links MAC addresses to specific network interfaces for enhanced network security.
## Content Addressable Memory (CAM) Table
Used to store information about the MAC addresses that are available on any given port of the switch.
## Persistent (Sticky) MAC Learning
Feature in network por security where the switch automatically learns and associates MAC addresses with specific interfaces.
## 802.1x Protocol
Standardized framework that is used for port-based authentication for both wired and wireless networks.
802.1x is top-notch defense against unauthorized access on the network.
- Supplicant: Client requesting access.
- Authenticator: Device which the client is trying to access the network.
- Authentication Server.
**RADIUS**: Cross-platform
**TACACS+**: Cisco-proprietary protocol
## Extensible Authentication Protocol
Series of protocol used for authentication.
- Simple Passwords
- Digital Certificates
- Public Key Infrastructure (PKI)
Variants:
- **EAP-MD5**: Utilizes simple passwords as the challenge handshake authentication process to provide remote access authentication.
- **EAP-TLS**: Uses public key infrastructure with a digital certificate being installed on both the client and the server as the method of authentication.
- **EAP-TTLS**: Requires a digital certificate on the server, but no on the client.
- **EAP-FAST**: Uses a protected access credential, instead of a certificate, to establish mutual authentication between devices.
- **PEAP**: Supports mutual authentication by using certificates and the Microsoft Active Directory databases for it to authenticate a password from the client.
- **EAP-LEAP**: Only works on Cisco-based devices.

## Wiretapping
Wiretapping, in the context of a wired network, refers to the act of connecting directly to the network's physical infrastructure (cables) to monitor and capture data traffic. It is a direct method to eavesdrop on communications.