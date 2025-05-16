## IPv6 Packet Header
![[IPv6HeaderIMG.png]]

- **Version**: This field contains a 4-bit binary value set to 0110 that identifies this as an IPv6 packet.
- **Traffic Class**: This 8-bit field is equivalent to the IPv4 Differentiated Services (DS) field.
- **Flow Label**: This 20-bit field suggests that all packets with the same flow label receive the same type of handling by routers.
- **Payload Length**: This 16-bit field indicates the length of the data portion or payload of the IPv6 packet.
- **Next Header**: This 8-bit field is equivalent to the IPv4 Protocol field. It indicates the data payload type that the packet is carrying, enabling the network layer to pass the data to the appropriate upper-layer protocol.
- **Hop Limit**: This 8-bit field replaces the IPv4 TTL field. This value is decremented by a value of 1 by each router that forwards the packet. When the counter reaches 0, the packet is discarded, and an ICMPv6 Time Exceeded message is forwarded to the sending host, indicating that the packet did not reach its destination because the hop limit was exceeded.