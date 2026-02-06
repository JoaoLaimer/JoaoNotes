## Wired Equivalent Privacy (WEP)
Outdated 1999 wireless security standard meant to match wired LAN security for wireless networks. WEP uses a fixed encryption key for all devices on the same network to secure messages.
- 64-bit WEP: 40 bits of key data and 24 of IV.
- 128-bit WEP: 104 bits of key data and 24 of IV.
WEP is insecure because of the 24-bit IV and should be avoided.
### IV Attacks
Initialization vector is a number used by encryption systems. When an encryption system reuses the same IV, an IV attack can discover the IV. WEP, uses a small 24-bit number for IV making WEP easy to crack.
## Wi-Fi Protected Access (WPA)
Introduced in 2003 as a temporary improvement over WEP while the more robust IEEE 802.11i standard was in development.
Improved security with TKIP, which generates new 128-bit keys for each packet, eliminating WEP's key-reuse vulnerabilities.
Due to TKIP vulnerabilities, WPA was susceptible to cryptographic attacks, underscoring the need for advanced wireless security.
Insecure because of the lack of sufficient data integrity checks in the TKIP implementation.
### WPA-Personal/WPA-PSK (Pre-shared key)
Designed for home, small office and basic uses and does not require an authentication server. Each wireless network device encrypts the network traffic,
## Wi-Fi Protected Access 2 (WPA2)
Improved data protection and network access control by addressing weaknesses in WPA version.
Replaced WPA's TKIP with AES and adopted CCMP for stronger encryption.
Counter Cipher Mode with Block Chaining Message Authentication Code Protocol (CCMP)
Switching to WPA2 provides stronger encryption and Introduces Message Integrity Code (MIC) for integrity checking.
The WPA2-PSK uses a passphrase to create a key, called Pairwise Master Key (PMK), to encrypt communications. The 4-way handshake is part WPA2 standard, using a pre-shared key (PSK)
## WPA3
Latest version using AES encryption and introducing new features like SAE, Enhanced Open, updated cryptographic protocols, and management protection frames.
Replaced WPA2 standard, 4-way handshake pre-shared key (PSK) that was repplaced with the Diffie-Hellman key agreement.
### Simultaneous Authentication of Equals (SAE)
Enhances security by offering a key establishment protocol to guard against offline dictionary attacks.
## Enhanced Open/Opportunistic Wireless Encryption (OWE)
Used for open authentication. Enhanced Open improves user privacy and security by guarding against eavesdropping attacks in public Wi-Fi settings.
### Cryptographic Protocol
Uses the newer AES GCMP.
#### Galois Counter Mode Protocol (GCMP)
Supports 128-bit AES for personal networks and 192-bit AES for enterprise networks with WPA3.
### Management Protection Frames
Required to protect network from key recovery attacks.
- Eavesdropping
- Forging
- Tampering
## Authentication, Authorization and Accounting (AAA) Protocol
Plays a vital role in network security by centralizing user authentication to permit only authorized users to access network resources
### Remote Authentication Dial-IN User Service (RADIUS)
Client/server protocol offering AAA services for network users.
RADIUS is used for secure network access, confirming user identities via a central server and enforcing predefined access rules.
Aids in monitoring user activity to ensure accountability and security policy enforcement.
### Terminal Access Controller Access-Control System Plus (TACACS+)
Separates the functions of AAA to allow for a more granular control over processes.
Uses TCP and encrypts authentication for improved security over older AAA protocols.
## Authentication Protocols
Confirm user identity for network security and authorized access.
### Extensible Authentication Protocol (EAP)
Authentication framework that supports multiple authentication methods.
### Protected Extensible Authentication Protocol (PEAP)
Authentication protocol that secures EAP within an encrypted and authenticated TLS tunnel.
Certificate (client and server)
## Extensible Authentication Protocol-Tunneled Transport Layer Security (EAP-TTLS)
Authentication protocol that extends TLS support across multiple platforms.
Certificate (server)

## Extensible Authentication Protocol-Flexible Authentication via Secure Tunneling (EAP-FAST)
Developed by Cisco, it enables secure re-authentication while roaming within a network without full authentication each time.
Developed to replace LEAP due to security vulnerabilities in the latter.