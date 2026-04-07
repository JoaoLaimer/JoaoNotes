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
**RADIUS**: Cross-platform (UDP)
**TACACS+**: Cisco-proprietary protocol (TCP)
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

> Enterprise mode requires an 802.1X server. EAP-FAST supports PACs. PEAP and EAP-TTLS require a certificate on the 802.1X server. EAP-TLS also uses TLS, but it requires certificates on both the 802.1X server and each of the clients. An 802.1X server provides port-based authentication, ensuring that only authorized clients can connect to a device or a network. It prevents rogue devices from connecting.
## Wiretapping
Wiretapping, in the context of a wired network, refers to the act of connecting directly to the network's physical infrastructure (cables) to monitor and capture data traffic. It is a direct method to eavesdrop on communications.

## Password Authentication Protocol (PAP)
Primarily used with dial-up connection, uses Point-to-Point Protocol (PPP) to authenticate clientes. PAP sends passwords over a network in cleartext, representing a considerable security risks. 
## Challenge Handshake Authentication Protocol (CHAP)
Also uses PPP and authenticate remote users, but is more secure than PAP. The client and server both know a shared secret. The client sends a hashed password combining it with a nonce (number used once) provided by the server.

