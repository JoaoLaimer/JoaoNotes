## 15.1 Application, Presentation, and Session
### 15.1.1 Application Layer
Based on the TCP/IP model, the upper three layers of the OSI model (application, presentation, and session) define functions of the TCP/IP application layer.
### 15.1.2 Presentation and Session Layer
**Presentation Layer**
The presentation layer has three primary functions:
- Formatting, or presenting, data at the source device into a compatible format for receipt by the destination device.
- Compressing data in a way that can be decompressed by the destination device.
- Encrypting data for transmission and decrypting data upon receipt.
The presentation layer formats data for the application layer, and it sets standards for file formats (JPG,MOV, GIF, etc.).
**Session Layer**
As the name implies, functions at the session layer create and maintain dialogs between source and destination applications. The session layer handles the exchange of information to initiate dialogs, keep them active, and to restart sessions that are disrupted or idle for a long period of time.

### 15.1.3 TCP/IP Application Layer Protocols
**Name System**
**DNS - Domain Name System (or Service)**
- TCP, UDP 53
- Translates domain names, such as cisco.com, into IP addresses.
**Host Config**
**BOOTP - Bootstrap Protocol**
- UDP client 68, server 67
- Enables a diskless workstation to discover its own IP address, the IP address of a BOOTP server on the network, and a file to be loaded into memory to boot the machine
- BOOTP is being superseded by DHCP

**DHCP - Dynamic Host Configuration Protocol**
- UDP client 68, server 67
- Dynamically assigns IP addresses to be re-used when no longer needed

**Email**
**SMTP - Simple Mail Transfer Protocol**
- TCP 25
- Enables clients to send email to a mail server
- Enables servers to send email to other servers

**POP3 - Post Office Protocol**
- TCP 110
- Enables clients to retrieve email from a mail server
- Downloads the email to the local mail application of the client

**IMAP - Internet Message Access Protocol**
- TCP 143
- Enables clients to access email stored on a mail server
- Maintains email on the server

**File Transfer**
**FTP - File Transfer Protocol**
- TCP 20 to 21
- Sets rules that enable a user on one host to access and transfer files to and from another host over a network
- FTP is a reliable, connection-oriented, and acknowledged file delivery protocol

**TFTP - Trivial File Transfer Protocol**
- UDP client 69
- A simple, connectionless file transfer protocol with best-effort, unacknowledged file delivery
- It uses less overhead than FTP

**Web**
**HTTP - Hypertext Transfer Protocol**
- TCP 80, 8080
- A set of rules for exchanging text, graphic images, sound, video, and other multimedia files on the World Wide Web

**HTTPS - HTTP Secure**
- TCP, UDP 443
- The browser uses encryption to secure HTTP communications
- Authenticates the website to which you are connecting your browser

### 15.2.1 Client-Server Model
Client and server processes are considered to be in the application layer. The client begins the exchange by requesting data from the server, which responds by sending one or more streams of data to the client. Application layer protocols describe the format of the requests and responses between clients and servers.

### 15.2.2 Peer-to-Peer Networks
In the peer-to-peer (P2P) networking model, the data is accessed from a peer device without the use of a dedicated server.
The P2P network model involves two parts: P2P networks and P2P applications. Both parts have similar features, but in practice work quite differently.
In a P2P network, two or more computers are connected via a network and can share resources (such as printers and files) without having a dedicated server. Every connected end device (known as a peer) can function as both a server and a client. In a peer-to-peer exchange, both devices are considered equal in the communication process.

### 15.2.3 Peer-to-Peer Applications
P2P applications require that each end device provide a user interface and run a background service.

Some P2P applications use a hybrid system where resource sharing is decentralized, but the indexes that point to resource locations are stored in a centralized directory. In a hybrid system, each peer accesses an index server to get the location of a resource stored on another peer.

### 15.2.4 Common P2P Applications
Common P2P networks include the following:
- BitTorrent
- Direct Connect
- eDonkey
- Freenet
Some P2P applications are based on the Gnutella protocol, where each user shares whole files with other users. As shown in the figure, Gnutella-compatible client software allows users to connect to Gnutella services over the internet, and to locate and access resources shared by other Gnutella peers. Many Gnutella client applications are available, including μTorrent, BitComet, DC++, Deluge, and emule.

Clients use a torrent file to locate other users who have pieces that they need so that they can then connect directly to them. This file also contains information about tracker computers that keep track of which users have specific pieces of certain files. Clients ask for pieces from multiple users at the same time. This is known as a swarm and the technology is called BitTorrent. BitTorrent has its own client. But there are many other BitTorrent clients including uTorrent, Deluge, and qBittorrent.