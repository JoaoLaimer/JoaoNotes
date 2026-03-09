## 14.1 Transportation of Data
### 14.1.1 Role of the Transport Layer
The transport layer is responsible for logical communications between applications running on different hosts. This may include services such as establishing a temporary session between two hosts and the reliable transmission of information for an application.
The transport layer has no knowledge of the destination host type, the type of media over which the data must travel, the path taken by the data, the congestion on a link, or the size of the network.

The transport layer includes two protocols:

- Transmission Control Protocol (TCP)
- User Datagram Protocol (UDP)

### 14.1.2 Transport Layer Responsibilities
The transport layer has many responsibilities:
- **Tracking Individual Conversations**: Each set of data flowing between a source application and a destination application is known as a conversation and is tracked separately. It is the responsibility of the transport layer to maintain and track these multiple conversations. Most networks have a limitation on the amount of data that can be included in a single packet. Therefore, data must be divided into manageable pieces.
- **Segmenting Data and Reassembling Segments**: It is the transport layer responsibility to divide the application data into appropriately sized blocks. The transport layer divides the data into smaller blocks (i.e., segments or datagrams) that are easier to manage and transport.
- **Add Header Information**: The transport layer protocol also adds header information containing binary data organized into several fields to each block of data. It is the values in these fields that enable various transport layer protocols to perform different functions in managing data communication. The transport layer ensures that even with multiple application running on a device, all applications receive the correct data.
- **Identifying the Applications**: The transport layer must be able to separate and manage multiple communications with different transport requirement needs. To pass data streams to the proper applications, the transport layer identifies the target application using an identifier called a port number.
- **Conversation Multiplexing**: The transport layer uses segmentation and multiplexing to enable different communication conversations to be interleaved on the same network. Error checking can be performed on the data in the segment, to determine if the segment was altered during transmission.

### 14.1.3 Transport Layer Protocols
Transport layer protocols specify how to transfer messages between hosts, and are responsible for managing reliability requirements of a conversation. The transport layer includes the TCP and UDP protocols.
### 14.1.4 Transmission Control Protocol (TCP)
TCP is considered a reliable, full-featured transport layer protocol, which ensures that all of the data arrives at the destination. TCP includes fields which ensure the delivery of the application data. These fields require additional processing by the sending and receiving hosts.
TCP provides reliability and flow control using these basic operations:
- Number and track data segments transmitted to a specific host from a specific application
- Acknowledge received data
- Retransmit any unacknowledged data after a certain amount of time
- Sequence data that might arrive in wrong order
- Send data at an efficient rate that is acceptable by the receiver
In order to maintain the state of a conversation and track the information, TCP must first establish a connection between the sender and the receiver. This is why TCP is known as a connection-oriented protocol.

### 14.1.5 User Datagram Protocol (UDP)
UDP is a simpler transport layer protocol than TCP. It does not provide reliability and flow control, which means it requires fewer header fields. Because the sender and the receiver UDP processes do not have to manage reliability and flow control, this means UDP datagrams can be processed faster than TCP segments. UDP provides the basic functions for delivering datagrams between the appropriate applications, with very little overhead and data checking.
UDP is a connectionless protocol. Because UDP does not provide reliability or flow control, it does not require an established connection. Because UDP does not track information sent or received between the client and server, UDP is also known as a stateless protocol.
UDP is also known as a best-effort delivery protocol because there is no acknowledgment that the data is received at the destination.

### 14.1.6 The Right Transport Layer Protocol for the Right Application
Some applications can tolerate some data loss during transmission over the network, but delays in transmission are unacceptable. For these applications, UDP is the better choice because it requires less network overhead. UDP is preferable for applications such as Voice over IP (VoIP). Acknowledgments and retransmission would slow down delivery and make the voice conversation unacceptable.

UDP is also used by request-and-reply applications where the data is minimal, and retransmission can be done quickly. For example, Domain Name System (DNS) uses UDP for this type of transaction.

For example, if one or two segments of a live video stream fail to arrive, it creates a momentary disruption in the stream. This may appear as distortion in the image or sound, but may not be noticeable to the user.

For other applications it is important that all the data arrives and that it can be processed in its proper sequence. For these types of applications, TCP is used as the transport protocol.

Real-time video and voice usually use UDP, but may also use TCP, or both UDP and TCP. A video conferencing application may use UDP by default, but because many firewalls block UDP, the application can also be sent over TCP.

**UDP**:
Required protocol properties:  
- Fast
- Low overhead
- Does not require acknowledgements
- Does not resend lost data
- Delivers data as it arrives

**TCP**:
Required protocol properties:  
- Reliable
- Acknowledges data
- Resends lost data
- Delivers data in sequenced order

## 14.2 TCP Overview
### 14.2.1 TCP Features
TCP provides the following services:
- **Establishes a Session** - TCP is a connection-oriented protocol that negotiates and establishes a permanent connection (or session) between source and destination devices prior to forwarding any traffic. Through session establishment, the devices negotiate the amount of traffic that can be forwarded at a given time, and the communication data between the two can be closely managed.
- **Ensures Reliable Delivery** - For many reasons, it is possible for a segment to become corrupted or lost completely, as it is transmitted over the network. TCP ensures that each segment that is sent by the source arrives at the destination.
- **Provides Same-Order Delivery** - Because networks may provide multiple routes that can have different transmission rates, data can arrive in the wrong order. By numbering and sequencing the segments, TCP ensures segments are reassembled into the proper order.
- **Supports Flow Control** - Network hosts have limited resources (i.e., memory and processing power). When TCP is aware that these resources are overtaxed, it can request that the sending application reduce the rate of data flow. This is done by TCP regulating the amount of data the source transmits. Flow control can prevent the need for retransmission of the data when the resources of the receiving host are overwhelmed.

For more information on TCP, search the internet for the RFC 793.

### 14.2.2 TCP Header
TCP is a stateful protocol which means it keeps track of the state of the communication session. To track the state of a session, TCP records which information it has sent and which information has been acknowledged. The stateful session begins with the session establishment and ends with the session termination.
A TCP segment adds 20 bytes (i.e., 160 bits) of overhead when encapsulating the application layer data. The figure shows the fields in a TCP header.
![[Pasted image 20251126111010.png]]
### 14.2.3 TCP Header Fields

| TCP Header Fields  | Description                                                                                                  |
| ------------------ | ------------------------------------------------------------------------------------------------------------ |
| Source Port        | A 16-bit field used to identify the source application by port number.                                       |
| Destination Port   | A 16-bit field used to identify the destination application by port number.                                  |
| Sequence Number    | A 32-bit field used for data reassembly purposes.                                                            |
| Acknowledge Number | A 32-bit field used to indicate that data has been received and the next byte expected from the source.      |
| Header Lenght      | A 4-bit field known as "data offset" that indicates the length of the TCP segment header.                    |
| Reserved           | A 6-bit field that is reserved for future use.                                                               |
| Control bits       | A 6-bit field that includes bit codes, or flags, which indicate the purpose and function of the TCP segment. |
| Window Size        | A 16-bit field used to indicate the number of bytes that can be accepted at one time.                        |
| Checksum           | A 16-bit field used for error checking of the segment header and data.                                       |
| Urgent             | A 16-bit field used to indicate if the contained data is urgent.                                             |
### 14.2.4 Applications that use TCP
- FTP
- SMTP
- HTTP
- SSH

### 14.3 UDP Overview
### 14.3.1 UDP Features
UDP features include the following:
- Data is reconstructed in the order that it is received.
- Any segments that are lost are not resent.
- There is no session establishment.
- The sending is not informed about resource availability.
### 14.3.2 UDP Header
UDP is a stateless protocol. If reliability is required when using UDP as the transport protocol, it must be handled by the application.
The blocks of communication in UDP are called datagrams, or segments. These datagrams are sent as best effort by the transport layer protocol.
The UDP header is far simpler than the TCP header because it only has four fields and requires 8 bytes (i.e., 64 bits). The figure shows the fields in a UDP header.
![[Pasted image 20251126171631.png]]
### 14.3.3 UDP Header Fields

| UDP Header Field  | Description                                                                 |
| ----------------- | --------------------------------------------------------------------------- |
| Source Port       | A 16-bit field used to identify the source application by port number.      |
| Destinantion Port | A 16-bit field used to identify the destination application by port number. |
| Lenght            | A 16-bit field that indicates the length of the UDP datagram header.        |
| Checksum          | A 16-bit field used for error checking of the datagram header and data.     |

### 14.3.4 Applications that use UDP
There are three types of applications that are best suited for UDP:
- **Live video and multimedia applications** - These applications can tolerate some data loss, but require little or no delay. Examples include VoIP and live streaming video.
- **Simple request and reply applications** - Applications with simple transactions where a host sends a request and may or may not receive a reply. Examples include DNS and DHCP.
- **Applications that handle reliability themselves** - Unidirectional communications where flow control, error detection, acknowledgments, and error recovery is not required, or can be handled by the application. Examples include SNMP and TFTP.
- DHCP
- DNS
- SNMP
- TFTP
- VoIP
- Video
Although DNS and SNMP use UDP by default, both can also use TCP. DNS will use TCP if the DNS request or DNS response is more than 512 bytes, such as when a DNS response includes many name resolutions. Similarly, under some situations the network administrator may want to configure SNMP to use TCP.

## 14.4 Port Numbers
The TCP and UDP header fields identify a source and destination application port number.
The source port number is associated with the originating application on the local host whereas the destination port number is associated with the destination application on the remote host.

### 14.4.2 Socket Pairs
The source and destination ports are placed within the segment. The segments are then encapsulated within an IP packet. The IP packet contains the IP address of the source and destination. The combination of the source IP address and source port number, or the destination IP address and destination port number is known as a socket.

The socket is used to identify the server and service being requested by the client. A client socket might look like this, with 1099 representing the source port number: 192.168.1.5:1099

Sockets enable multiple processes, running on a client, to distinguish themselves from each other, and multiple connections to a server process to be distinguished from each other.

### 14.4.3 Port Number Groups
The Internet Assigned Numbers Authority (IANA) is the standards organization responsible for assigning various addressing standards, including the 16-bit port numbers. The 16 bits used to identify the source and destination port numbers provides a range of ports from 0 through 65535.

| Port Group                   | Number Range   | Description                                                                                                                                                                                                                  |
| ---------------------------- | -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Well-Known Ports             | 0 to 1023      | Reserved for common or popular services and applications. Enables clients to easily identify the associated service required.                                                                                                |
| Registered Ports             | 1024 to 49151  | Ports assigned by IANA to a requesting entity to use. These processes are primarily individual applications that a user has chosen to install,  rather than common applications that would receive a Well-Known Port number. |
| Private and/or Dynamic Ports | 49152 to 65535 | Also known as ephemeral ports. Client OS usually assign port numbers dynamically when a connection to a service is initiated. Used to identify the client application during communication.                                  |
**Note:** Some client operating systems may use registered port numbers instead of dynamic port numbers for assigning source ports.

The table displays some common well-known port numbers and their associated applications.

| Port Number | Protocol | Application                                         |
| ----------- | -------- | --------------------------------------------------- |
| 20          | TCP      | File Transfer Protocol (FTP) - Data                 |
| 21          | TCP      | File Transfer Protocol (FTP) - Control              |
| 22          | TCP      | Secure Shell (SSH)                                  |
| 23          | TCP      | Telnet                                              |
| 25          | TCP      | Simple Mail Transfer Protocol (SMTP)                |
| 53          | UDP, TCP | Domain Name System (DNS)                            |
| 67          | UDP      | Dynamic Host Configuration Protocol (DHCP) - Server |
| 68          | UDP      | DHCP - Client                                       |
| 69          | UDP      | Trivial File Transfer Protocol (TFTP)               |
| 80          | TCP      | Hypertext Transfer Protocol (HTTP)                  |
| 110         | TCP      | Post Office Protocol Version 3 (POP3)               |
| 143         | TCP      | Internet Message Access Protocol (IMAP)             |
| 161         | UDP      | Simple Network Management Protocol (SNMP)           |
| 443         | TCP      | Hypertext Transfer Protocol Secure (HTTPS)          |
### 14.4.4 The netstat Command
Unexplained TCP connections can pose a major security threat. They can indicate that something or someone is connected to the local host. Sometimes it is necessary to know which active TCP connections are open and running on a networked host. Netstat is an important network utility that can be used to verify those connections.

By default, the **netstat** command will attempt to resolve IP addresses to domain names and port numbers to well-known applications. The **-n** option can be used to display IP addresses and port numbers in their numerical form.

## 14.5 TCP Communication Process
### 14.5.1 TCP Server Processes
An individual server cannot have two services assigned to the same port number within the same transport layer services.
An active server application assigned to a specific port is considered open, which means that the transport layer accepts, and processes segments addressed to that port. Any incoming client request addressed to the correct socket is accepted, and the data is passed to the server application. There can be many ports open simultaneously on a server, one for each active server application.

### 14.5.2 TCP Connection Establishment
The host client establishes the connection with the server using the three-way handshake process.
**Step 1. SYN**
	The initiating client requests a client-to-server communication session with the server.
**Step 2. ACK and SYN**
	The server acknowledges the client-to-server communication session and requests a server-to-client communication session.
**Step 3. ACK**
	The initiating client acknowledges the server-to-client communication session.
### 14.5.3 Session Termination
To terminate a single conversation supported by TCP, four exchanges are needed to end both sessions. Either the client or the server can initiate the termination.

**Step 1. FIN**
	When the client has no more data to send in the stream, it sends a segment with the FIN flag set.
**Step 2. ACK**
	The server sends an ACK to acknowledge the receipt of the FIN to terminate the session from client to server.
**Step 3. FIN**
	The server sends a FIN to the client to terminate the server-to-client session.
**Step 4. ACK**
	The client responds with an ACK to acknowledge the FIN from the server.

### 14.5.4 TCP Three-way Handshake Analysis
TCP is a full-duplex protocol, where each connection represents two one-way communication sessions. To establish the connection, the hosts perform a three-way handshake.

These are the functions of the three-way handshake:
- It establishes that the destination device is present on the network.
- It verifies that the destination device has an active service and is accepting requests on the destination port number that the initiating client intends to use.
- It informs the destination device that the source client intends to establish a communication session on that port number.

After the communication is completed the sessions are closed, and the connection is terminated. The connection and session mechanisms enable TCP reliability function.

The six bits in the Control Bits field of the TCP segment header are also known as flags. A flag is a bit that is set to either on or off.

The six control bits flags are as follows:
- **URG** - Urgent pointer field significant
- **ACK** - Acknowledgment flag used in connection establishment and session termination
- **PSH** - Push function
- **RST** - Reset the connection when an error or timeout occurs
- **SYN** - Synchronize sequence numbers used in connection establishment
- **FIN** - No more data from sender and used in session termination

## 14.6 Reliability and Flow Control
### 14.6.1 TCP Reliability - Guaranteed and Ordered Delivery
During session setup, an initial sequence number (ISN) is set. This ISN represents the starting value of the bytes that are transmitted to the receiving application. As data is transmitted during the session, the sequence number is incremented by the number of bytes that have been transmitted. This data byte tracking enables each segment to be uniquely identified and acknowledged. Missing segments can then be identified.
The ISN does not begin at one but is effectively a random number.

**TCP Segments Are Reordered at the Destination**

The receiving TCP process places the data from a segment into a receiving buffer. Segments are then placed in the proper sequence order and passed to the application layer when reassembled. Any segments that arrive with sequence numbers that are out of order are held for later processing. Then, when the segments with the missing bytes arrive, these segments are processed in order.

### 14.6.3 TCP Reliability - Data Loss and Retransmission
The sequence (SEQ) number and acknowledgement (ACK) number are used together to confirm receipt of the bytes of data contained in the transmitted segments.
The SEQ number identifies the first byte of data in the segment being transmitted. TCP uses the ACK number sent back to the source to indicate the next byte that the receiver expects to receive. This is called expectational acknowledgement.
Prior to later enhancements, TCP could only acknowlege the next byte expected.

Today hosts employ an option TCP feature called selective acknowledgment (SACK), negotiated during the three-way handshake. If both hosts support SACK, the receiver can explicitly acknowledge which segments (bytes) were received including any discontinuous segments.
### 14.6.5 TCP Flow Control - Window Size and Acknowledgments
TCP also provides mechanisms for flow control. Flow control is the amount of data that the destination can receive and process reliably. Flow control helps maintain the reliability of TCP transmission by adjusting the rate of data flow between source and destination for a given session. To accomplish this, the TCP header includes a 16-bit field called the window size
The window size determines the number of bytes that can be sent before expecting an acknowledgment. The acknowledgment number is the number of the next expected byte.

The initial window size is agreed upon when the TCP session is established during the three-way handshake. The source device must limit the number of bytes sent to the destination device based on the window size of the destination.

A destination sending acknowledgments as it processes bytes received, and the continual adjustment of the source send window, is known as sliding windows.

**Note:** Devices today use the sliding windows protocol. The receiver typically sends an acknowledgment after every two segments it receives. The number of segments received before being acknowledged may vary. The advantage of sliding windows is that it allows the sender to continuously transmit segments, as long as the receiver is acknowledging previous segments. 

### 14.6.6 TCP Flow Control - Maximum Segment Size (MSS)
The MSS is part of the options field in the TCP header that specifies the largest amount of data, in bytes, that a device can receive in a single TCP segment. The MSS size does not include the TCP header. The MSS is typically included during the three-way handshake.

A common MSS is 1,460 bytes when using IPv4. A host determines the value of its MSS field by subtracting the IP and TCP headers from the Ethernet maximum transmission unit (MTU). On an Ethernet interface, the default MTU is 1500 bytes. Subtracting the IPv4 header of 20 bytes and the TCP header of 20 bytes, the default MSS size will be 1460 bytes.

### 14.6.7 TCP Flow Control - Congestion Avoidance
When congestion occurs on a network, it results in packets being discarded by the overloaded router. When packets containing TCP segments do not reach their destination, they are left unacknowledged. By determining the rate at which TCP segments are sent but not acknowledged, the source can assume a certain level of network congestion.
Whenever there is congestion, retransmission of lost TCP segments from the source will occur. If the retransmission is not properly controlled, the additional retransmission of the TCP segments can make the congestion even worse.

## 14.7 UDP Communication
### 14.7.1 UDP Low Overhead versus Reliability
UDP does not establish a connection. UDP provides low overhead data transport because it has a small datagram header and no network management traffic.
### 14.7.2 UDP Datagram Reassembly
UDP simply reassembles the data in the order that it was received and forwards it to the application. If the data sequence is important to the application, the application must identify the proper sequence and determine how the data should be processed.

### 14.7.3 UDP Server Processes and Requests
Like TCP-based applications, UDP-based server applications are assigned well-known or registered port numbers, as shown in the figure. When these applications or processes are running on a server, they accept the data matched with the assigned port number. When UDP receives a datagram destined for one of these ports, it forwards the application data to the appropriate application based on its port number.

### 14.7.4 UDP Client Processes
**Clients Sending UDP Requests**

Client 1 is sending a DNS request while Client 2 is requesting RADIUS authentication services of the same server.

**UDP Request Destination Ports**
Client 1 is sending a DNS request using the well-known destination port 53 while Client 2 is requesting RADIUS authentication services using the registered destination port 1812.

**UDP Request Source Ports**
The requests of the clients dynamically generate source port numbers. In this case, Client 1 is using source port 49152 and Client 2 is using source port 51152.

**UDP Response Destination**
When the server responds to the client requests, it reverses the destination and source ports of the initial request. In the Server response to the DNS request is now destination port 49152 and the RADIUS authentication response is now destination port 51152.

**UDP Response Source Ports**
The source ports in the server response are the original destination ports in the initial requests.
