## 14.1 Transportation of Data
### 14.1.1 Role of the Transport Layer
The transport layer is responsible for logical communications between applications running on different hosts. This may include services such as establishing a temporary session between two hosts and the reliable transmission of information for an application.
The transport layer has no knowledge of the destination host type, the type of media over which the data must travel, the path taken by the data, the congestion on a link, or the size of the network.

The transport layer includes two protocols:

- Transmission Control Protocol (TCP)
- User Datagram Protocol (UDP)

### 14.1.2 Transport Layer Responsibilities
The transport layer has many resposibilities:
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