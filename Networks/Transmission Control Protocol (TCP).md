TCP is considered a reliable, full-featured transport layer protocol, which ensures that all of the data arrives at the destination. TCP includes fields which ensure the delivery of the application data. These fields require additional processing by the sending and receiving hosts.
**Note**: TCP divides data into segments.
TCP provides reliability and flow control using these basic operations:
- Number and track data segments transmitted to a specific host from a specific application
- Acknowledge received data
- Retransmit any unacknowledged data after a certain amount of time
- Sequence data that might arrive in wrong order
- Send data at an efficient rate that is acceptable by the receiver
TCP is used as the transport protocol. For example, applications such as databases, web browsers, and email clients, require that all data that is sent arrives at the destination in its original condition. Any missing data could corrupt a communication, making it either incomplete or unreadable. For example, it is important when accessing banking information over the web to make sure all the information is sent and received correctly.

Application developers must choose which transport protocol type is appropriate based on the requirements of the applications. Video may be sent over TCP or UDP. Applications that stream stored audio and video typically use TCP. The application uses TCP to perform buffering, bandwidth probing, and congestion control, in order to better control the user experience.
Required protocol properties:  
- Reliable
- Acknowledges data
- Resends lost data
- Delivers data in sequenced order
In addition to supporting the basic functions of data segmentation and reassembly, TCP also provides the following services:

- **Establishes a Session -** TCP is a connection-oriented protocol that negotiates and establishes a permanent connection (or session) between source and destination devices prior to forwarding any traffic. Through session establishment, the devices negotiate the amount of traffic that can be forwarded at a given time, and the communication data between the two can be closely managed.
- **Ensures Reliable Delivery -** For many reasons, it is possible for a segment to become corrupted or lost completely, as it is transmitted over the network. TCP ensures that each segment that is sent by the source arrives at the destination.
- **Provides Same-Order Delivery -** Because networks may provide multiple routes that can have different transmission rates, data can arrive in the wrong order. By numbering and sequencing the segments, TCP ensures segments are reassembled into the proper order.
- **Supports Flow Control -** Network hosts have limited resources (i.e., memory and processing power). When TCP is aware that these resources are overtaxed, it can request that the sending application reduce the rate of data flow. This is done by TCP regulating the amount of data the source transmits. Flow control can prevent the need for retransmission of the data when the resources of the receiving host are overwhelmed.

For more information on TCP, search the internet for the RFC 793.

## TCP Header

A TCP segment adds 20 bytes (i.e., 160 bits) of overhead when encapsulating the application layer data. The figure shows the fields in a TCP header.

| TCP Header Field      | Size   | Description                                                                               |
| --------------------- | ------ | ----------------------------------------------------------------------------------------- |
| Source Port           | 16-bit | Identify the source application by port numbers.                                          |
| Destination Port      | 16-bit | Identify the destination application by port number.                                      |
| Sequence Number       | 32-bit | Data reassembly purposes.                                                                 |
| Acknowledgment Number | 32-bit | Indicate that data has been received and the next byte expected from the source.          |
| Header Length         | 4-bit  | Known as "data offset" that indicates the length of the TCP segment header.               |
| Reserved              | 6-bit  | Reserved for future use.                                                                  |
| Control Bit           | 6-bit  | Includes bit codes, or flags, which indicate the purpose and function of the TCP segment. |
| Window size           | 16-bit | Indicates the number of bytes that can be accepted at one time.                           |
| Checksum              | 16-bit | Error checking of the segment header and data.                                            |
| Urgent                | 16-bit | Used to indicate if the contained data is urgent.                                         |
## Application that use TCP
- **FTP**
- **SMTP**
- **HTTP**
- **SSH**

# Three Way Handshake
In some cultures, when two persons meet, they often greet each other by shaking hands. Both parties understand the act of shaking hands as a signal for a friendly greeting. Connections on the network are similar. In TCP connections, the host client establishes the connection with the server using the three-way handshake process.

The six bits in the Control Bits field of the TCP segment header are also known as flags. A flag is a bit that is set to either on or off.

The six control bits flags are as follows:

- **URG** - Urgent pointer field significant
- **ACK** - Acknowledgment flag used in connection establishment and session termination
- **PSH** - Push function
- **RST** - Reset the connection when an error or timeout occurs
- **SYN** - Synchronize sequence numbers used in connection establishment
- **FIN** - No more data from sender and used in session termination
### Session Establishment
**Step 1. SYN**: The initiating client requests a client-to-server communication session with the server.
**Step 2. ACK and SYN**: The server acknowledges the client-to-server communication session and requests a server-to-client communication session.
**Step 3. ACK**: The initiating client acknowledges the server-to-client communication session.
### Session Termination
**Step 1. FIN**: When the client has no more data to send in the stream, it sends a segment with the FIN flag set.
**Step 2. ACK**: The server sends an ACK to acknowledge the receipt of the FIN to terminate the session from client to server.
**Step 3. FIN**: The server sends a FIN to the client to terminate the server-to-client session.
**Step 4. ACK**: The client responds with an ACK to acknowledge the FIN from server.
## TCP Sequence Numbers
During session setup, an initial sequence number (ISN) is set. This ISN represents the starting value of the bytes that are transmitted to the receiving application. As data is transmitted during the session, the sequence number is incremented by the number of bytes that have been transmitted. This data byte tracking enables each segment to be uniquely identified and acknowledged. Missing segments can then be identified.
The receiving TCP process places the data from a segment into a receiving buffer. Segments are then placed in the proper sequence order and passed to the application layer when reassembled. Any segments that arrive with sequence numbers that are out of order are held for later processing. Then, when the segments with the missing bytes arrive, these segments are processed in order.
## Windows Size and Acknowledgements
TCP also provides mechanisms for flow control. Flow control is the amount of data that the destination can receive and process reliably. Flow control helps maintain the reliability of TCP transmission by adjusting the rate of data flow between source and destination for a given session. To accomplish this, the TCP header includes a 16-bit field called the window size.
The window size determines the number of bytes that can be sent before expecting an acknowledgment. The acknowledgment number is the number of the next expected byte.
The MSS is part of the options field in the TCP header that specifies the largest amount of data, in bytes, that a device can receive in a single TCP segment. The MSS size does not include the TCP header. The MSS is typically included during the three-way handshake.
A common MSS is 1,460 bytes when using IPv4. A host determines the value of its MSS field by subtracting the IP and TCP headers from the Ethernet maximum transmission unit (MTU). On an Ethernet interface, the default MTU is 1500 bytes. Subtracting the IPv4 header of 20 bytes and the TCP header of 20 bytes, the default MSS size will be 1460 bytes.
## Congestion Avoidance
When congestion occurs on a network, it results in packets being discarded by the overloaded router. When packets containing TCP segments do not reach their destination, they are left unacknowledged. By determining the rate at which TCP segments are sent but not acknowledged, the source can assume a certain level of network congestion.