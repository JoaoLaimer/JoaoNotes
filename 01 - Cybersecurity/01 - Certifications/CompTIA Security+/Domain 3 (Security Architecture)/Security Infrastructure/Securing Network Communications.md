## Virtual Private Network (VPN)
Extends a private network over a public one, enabling users to security send and receive data.
### Site-to-Site
Establishes secure tunnels over the public internet for interconnecting remote sites.
### Client-to-Site
Connects individual devices directly to the organization's headquarters, enabling remote users to access the network.
### Full Tunnel
Maximizes security by encrypting all traffic to the headquarters while integrating clients with the network
## Split Tunnel
Divides traffic and network requests and then routes them to the appropriate network.
### Clientless VPN
Secures remote access thought browser-based VPN tunnels without needing client software or hardware configurations.
### Transport Layer Security (TLS)
A protocol that provides cryptographic security for secure web browsing and data transfer.
### Transmission Control Protocol
Used by TLS to establish secure connection between a client and a server, but it may slow down the connection
### Datagram Transport Layer Security (DTLS)
A UDP-based version of TLS protocol that offers the same security level as TLS while maintaining faster operations.
DTLS ensures end-user security and protects against eavesdropping in clientless VPN connections.
## Internet Protocol Security (IPsec)
A protocol suite for secure communication through authentication and data encryption in IP networks.
- Confidentiality
- Integrity
- Authentication
- Anti-replay
Process:
1. Request to start Internet Key Exchange (IKE)
	PC1 initiates traffic to PC2, triggering IPSec tunnel creation by RTR1.
2. IKE Phase 1
	RTR1 and RTR2 negotiate security associations fot the IPSec IKE Phase 1 (ISAKMP) tunnel.
3. IKE Phase 2
	IKE Phase 2 establishes a tunnel within the tunnel.
4. Data transfer
	 Data transfer between PC1 and PC2 takes place securely
5. Tunnel termination
	Tunnel termination, including the deletion of IPsec security associations.
### Transport Mode
Employs the original IP header, ideal for client-to-site VPNs, and is advantageous when dealing with MTU constraints.
MTU (Maximum Transmission Unit) is set only at 1500 bytes and may cause fragmentation and VPN problems.
### Tunneling Mode
Employed for site-to-site VPNs and adds an extra header that can increase packet size and exceed the MTU.

At the destination site, the VPN concentrator removes the outer header, decrypts the content, and routes it internally.

In tunneling mode, packets are encapsulated within new ones, potentially exceeding the 1500-byte limit of MTU.

Site-to-Site VPNs may require support for jumbo frames above an MTU of 1500 bytes.

Lower the inner router's MTU to ~1400 bytes if jumbo frames cannot be utilized.

Adjusting the MTU to 9000 bytes is feasible in local area networks but not recommended for Internet use due to potential issues.

### Authentication Header (AH)
Offers connectionless data integrity and data origin authentication for IP datagrams using cryptographic hash as identification information.
### Encapsulating Security Payload (ESP)
Employed for providing authentication, integrity, replay protection, and data confidentiality by encrypting the packet's payload.

In tunneling mode, employ both the authentication header and the encapsulated security payload.
### Protocols
- **IPsec (Internet Protocol Security):** A suite of protocols used for securing IP traffic, providing authentication and encryption at the network layer. It is often used in Site-to-Site VPNs.
- **OpenVPN:** An open-source, versatile protocol that uses the OpenSSL library for encryption, offering high security and compatibility. Commonly uses UDP port 1194.
- **WireGuard:** A modern, high-performance VPN protocol known for being lightweight and fast while utilizing state-of-the-art cryptography. Uses UDP port 51820 by default.
- **SSTP (Secure Socket Tunneling Protocol):** A Microsoft-developed protocol that uses SSL/TLS (Port 443) to encapsulate traffic, allowing it to bypass most firewalls.
- **IKEv2 (Internet Key Exchange v2)**: Often paired with IPsec, this protocol is excellent for mobile devices due to its ability to reconnect quickly when switching between networks. Primarily uses UDP port 1701.
- **L2TP/IPsec (Layer 2 Tunneling Protocol):** Creates the tunnel (L2TP) and relies on IPsec for encryption.
- **PPTP (Point-to-Point Tunneling Protocol):** An older, less secure protocol. It is rarely used now due to known vulnerabilities, but it is still important to know for legacy compatibility