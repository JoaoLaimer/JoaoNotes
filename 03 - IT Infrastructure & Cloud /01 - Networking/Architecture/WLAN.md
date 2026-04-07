WLANs uses Radio Frequencies (RD) at the physical layer and MAC sublayer of the data link layer. IEEE has adopted the 802 LAN/MAN portfolio of computer network architecture standards. The two dominant 802 working groups are 802.3 Ethernet, which defined for wired LANs, nas 802.11 which defined for WLANs.
- WLANs support hosts that contend for acces on the RF media. 802.11 prescribes collision-avoidance (CSMA/CA) instead of collision-detection (CSMA/CD) for media access to proactively avoid collisions within the media.
- WLANs use a different frame format than wired LANs. It requires additional information in the Layer 2 header of the frame.![[WLANHeader.png]]
All 802.11 wireless frames contain the following fields:

- **Frame Control -** This identifies the type of wireless frame and contains subfields for protocol version, frame type, address type, power management, and security settings.
- **Duration -** This is typically used to indicate the remaining duration needed to receive the next frame transmission.
- **Address1 -** This usually contains the MAC address of the receiving wireless device or AP.
- **Address2 -** This usually contains the MAC address of the transmitting wireless device or AP.
- **Address3 -** This sometimes contains the MAC address of the destination, such as the router interface (default gateway) to which the AP is attached.
- **Sequence Control -** This contains information to control sequencing and fragmented frames.
- **Address4 -** This usually missing because it is used only in ad hoc mode.
- **Payload -** This contains the data for transmission.
- **FCS -** This is used for Layer 2 error control.

## CSMA/CA
WLANs are half-duplex, shared media configurations. Half-duplex means that only one client can transmit or receive at any given moment. Shared media means that wireless clients can all transmit an receive on the same radio channel.
This creates a problem because a wireless client cannot hear while it is sending, which makes it impossible to detect a collision. 
To resolve this problem, WLANs use carrier sense multiple access with collision avoidance (CSMA/CA) as the method to determine how and when to send data on the network. A wireless client does the following:\
1. Listens to the channel to see if it is idle, which means that is senses no other traffic is currently on the channel. The channel is also called the carrier.
2. Sends a ready to send (RTS) message to the AP to request dedicated access to the network.
3. Receives a clear to send (CTS) message from the AP granting access to send.
4. If the wireless client does not receive a CTS message, it waits a random amount of time before restarting the process.
5. After it receives the CTS, it transmits the data.
6. All transmissions are acknowledged. If a wireless client does not receive an acknowledgment, it assumes a collision occurred and restarts the process.
## Wireless Client and AP Association
For wireless devices to communicate over a network , they must first associate with an AP or wireless router. An important part of the 802.11 process is discovering a WLAN and subsequently connecting to it. 
- Discover a wireless AP
- Authenticate with AP
- Associate with AP
In order to associate, parameters must then be configured on the AP and subsequently on the client to enable the negotiation.
- **SSID** - The name of the available network. In larger organizations, each SSID is mapped to one VLAN.
- **Password** - This is required from the wireless client to authenticate to the AP.
- **Network Mode** - This refers to the 802.11a/b/g/n/ac/ad WLAN standards. APs and wireless routers can operate in a Mixed mode meaning that they can simultaneously support clients connecting via multiple standards.
- **Security Mode** - Security parameters settings, such as WEP, WPA, or WPA2.
- **Channel settings** - This refers to the frequency bands used to transmit wireless data. Wireless routers and APs can scan the radio frequency channels and automatically select an appropriate channel setting. 

A **wireless LAN controller (WLC)** can be configured to manage multiple lightweight access points (LWAPs). On the WLC, a network administrator can configure SSIDs, security, IP addressing, and other wireless network parameters in a centralized management environment.
## Passive and Active Discover Mode
Wireless devices must discover and connect to an AP or wireless router. Wireless clients connect to the AP using a scanning (probing) process. This process can be passive or active.
### Passive Mode
In passive mode, the AP openly advertises its service by periodically sending broadcast beacon frames containing the SSID, supported standards, and security settings. The primary purpose of the beacon is to allow wireless clients to learn which networks and APs are available in a given area. This allows the wireless clients to choose which network and AP to use.
## Active Mode
In active mode, wireless clients must know the name of the SSID. The wireless client initiates the process by broadcasting a probe request frame on multiple channels. The probe request includes the SSID name and standards supported. APs configured with the SSID will send a probe response that includes the SSID, supported standards, and security settings. Active mode may be required if an AP or wireless router is configured to not broadcast beacon frames.

A wireless client could also send a probe request without a SSID name to discover nearby WLAN networks. APs configured to broadcast beacon frames would respond to the wireless client with a probe response and provide the SSID name. APs with the broadcast SSID feature disabled do not respond.
## Infrastructure Mode
A wireless router or AP connects wireless clients to a wired distribution system.
## Ad hoc Mode
A wireless router or AP is not present. Two devices connect wireless in a peer-to-peer (P2P).
## Thethering
A variation of ad hoc, where a smartphone or tablet with cellular data access is used as a personal hotspot.
## The BSS (Basic Service Set)
BSA (Basic Service Area): Area where the signal of the AP works.
BSSID : Layer 2 mac address of the access point.

## The ESS (Extended Service Set)
BSAs connected to a distribution system.

## Secure WLAN

| Authentication Method          | Description                                                                                                                                       |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Wired Equivalent Privacy (WEP) | Original 802.11 specification (RC4) designed to secure wireless data with a static key. WEP is no longer recommended and should never be used.    |
| WI-FI Protected Access (WPA)   | A Wi-Fi Alliance standard that uses WEP, but secures the data with the much stronger Temporal Key Integrity Protocol (TKIP) encryption algorithm. |
| WPA2                           | WAP2 is the current industry standard for securing wireless networks. It uses the Advanced Encryption Standard (AES) for encryption.              |
| WPA3                           | All WPA3-enabled devices use the latest security methods and require the use of Protected Management Frames (PMF).                                |
#### Authenticating a User
- **Personal** - Intended for home or small office networks, users authenticate using a pre-shared key (PSK).
- **Enterprise** - Intended for enterprise networks but requires a Remote Authentication Dial-In User Service (RADIUS) authentication server.
#### Temporal Key Integrity Protocol (TKIP)
TKIP is the encryption method used by WPA. It uses WEP, but encrypts the Layer 2 payload using TKIP, and carries out a Message Integrity Check (MIC) in the encrypted packet to ensure the message has not been altered.
#### AES
It uses the Counter Cipher Mode with Block Chaining Message Authentication Code Protocol (CCMP) that allows destination hosts to recognize if the encrypted and non-encrypted bits have been altered.
### RADIUS
- **RADIUS Server IP address -** This is the reachable address of the RADIUS server.
- **UDP port numbers -** Officially assigned UDP ports 1812 for RADIUS Authentication, and 1813 for RADIUS Accounting, but can also operate using UDP ports 1645 and 1646, as shown in the figure.
- **Shared key -** Used to authenticate the AP with the RADIUS server.
### SSID Cloaking
APs and some wireless routers allow the SSID beacon frame to be disabled.
### MAC Address Filtering
An administrator can manually permit or deny clients wireless access based on their physical MAC address.

## WPA3
### WPA3-Personal
IN WPA2-Personal, threat actors can listen on the "handshake" between a wireless cleint and the AP and use a brute force attack to try and guess the PSK. WPA3-Personal thwarts this attack by using Simultaneous Authentication of Equals (SAE), a feature specified in the IEEE 802.11-2016. The PSK is never exposed, making it impossible for the threat actor to guess.
### WPA3-Enterprise
WPA3-Enterprise still uses 802.1X/EAP authentication. However. it requires the use of a 192-but cryptographic suite and eliminates the mixing of security protocols for previous 802.11 standards. WPA3-Enterprise adheres to the Commercial National Security Algorithm (CNSA) Suite.
### Open Networks
Open networks in WPA2 send user traffic in unauthenticated, clear text. In WPA3, open or public Wi-Fi networks still do not use any authentication. However, they do use Opportunistic Wireless Encryption (OWE) to encrypt all wireless traffic.
### IoT Onboarding
lthough WPA2 included Wi-Fi Protected Setup (WPS) to quickly onboard devices without configuring them first, WPS is vulnerable to a variety of attacks and is not recommended. Furthermore, IoT devices are typically headless, meaning they have no built-in GUI for configuration, and needed any easy way to get connected to the wireless network. The Device Provisioning Protocol (DPP) was designed to address this need. Each headless device has a hardcoded public key. The key is typically stamped on the outside of the device or its packaging as a Quick Response (QR) code. The network administrator can scan the QR code and quickly onboard the device. Although not strictly part of the WPA3 standard, DPP will replace WPS over time.