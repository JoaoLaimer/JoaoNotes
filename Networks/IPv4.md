## IPv4 Packet Header
![[IPv4HeaderIMG.png]]
- **Version**: Contains a 4-bit binary value set to 0100 that identifies this as an IPv4 packet.
- **Internet Header Length**: Formerly called the Type of Service (ToS) field, the DS field is an 8-bit field used to determine the priority of each packet. The six most significant bits of the DiffServ field are the Differentiated Services Code Point (DSCP). The last two bits are the Explicit Congestion Notification (ECN) bits.
- **Time-to-Live (TTL)**: Contains an 8-bit binary value that is used to limit the lifetime of a packet. The packet sender sets the initial TTL value, and it is decreased by one each time the packet is processed by a router. If the TTL field decrements to zero, the router discards the packet and sends an Internet Control Message Protocol (ICMP) Time Exceeded message to the source IP address.
- **Identification, Flag, and Fragment**: As an IP packet moves through the internet, it might need to cross a route that cannot handle the size of the packet.The packet will be divided, or fragmented, into smaller packets and reassembled later.These fields are used to fragment and reassemble packets.
- **Protocol**: Field is used to identify the next level protocol. This 8-bit binary value indicates the data payload type that the packet is carrying, which enables the network layer to pass the data to the appropriate upper-layer protocol. Common values include ICMP (1), TCP (6), and UDP (17).
- **Header checksum**: A value that is calculated based on the contents of the IP header. Used to determine if any errors have been introduced during transmission.
- **Options and Padding**: This is a field that varies in length from 0 to a multiple of 32 bits. If the option values are not a multiple of 32 bits, 0s are added, or padded, to ensure that this field contains a multiple of 32 bits.

