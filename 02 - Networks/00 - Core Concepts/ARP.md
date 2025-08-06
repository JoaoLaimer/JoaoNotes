The Address Resolution Protocol, or ARP, is what you need to map IPv4 addresses to MAC addresses. To send a packet to another host on the same local IPv4 network, a host must know the IPv4 address and the MAC address of the destination device. IPv4 addresses are either know or resolved by device name. However, MAC addresses must be discovered.
A device uses Address Resolution Protocol (ARP) to determine the destination MAC address of a local device when it knows its IPv4 address.
ARP provides two basic functions:
- Resolving IPv4 addresses to MAC addresses.
- Maintaining a table of IPv4 to MAC address mappings.
### ARP Operation
ARP messages are encapsulated directly within an Ethernet frame. There is no IPv4 header. The ARP request is encapsulated in an Ethernet frame using the following header information:
- **Destination MAC address** - This is a broadcast address FF-FF-FF-FF-FF-FF requiring all Ethernet NICs on the LAN with it's the request. If it's the reply, is the MAC address of the sender of the ARP request.
- **Source MAC address** - This is MAC address of the sender of the ARP request or ARP reply.
- **Type** - ARP messages have a type field of 0x806. This informs the NIC that the data portion of the frame needs to be passed to the ARP process.
Because ARP requests are broadcasts, they are flooded out all ports by the switch, except the receiving port.
Only the device that originally sent the ARP request will receive the unicast ARP reply.
If no device responds to the ARP request, the packet is dropped because a frame cannot be created.

1.  Who has `<DESTINATION-IP>`? Tell `<SOURCE-IP>`
2. `<DESTINATION-IP>` is at `<DESTINATION-MAC>`
3. The destination IP and MAC is stored in the source machine.
4. The source IP and MAC is stored in the destination machine.
**Note**: IPv6 uses a similar process to ARP for IPv4, known as ICMPv6 Neighbor Discovery (ND). IPv6 uses neighbor solicitation and neighbor advertisement messages, similar to IPv4 ARP requests and ARP replies.

## ARP Role in Remote Communications
When the destination IPv4 address is not on the same network as the source IPv4 address, the source device needs to send the frame to its default gateway. This is the interface of the local router. Whenever a source device has a packet with an IPv4 address on another network, it will encapsulate that packet in a frame using the destination MAC address of the router.

The IPv4 address of the default gateway is stored in the IPv4 configuration of the hosts. When a host creates a packet for a destination, it compares the destination IPv4 address and its own IPv4 address to determine if the two IPv4 addresses are located on the same Layer 3 network. If the destination host is not on its same network, the source checks its ARP table for an entry with the IPv4 address of the default gateway. If there is not an entry, it uses the ARP process to determine a MAC address of the default gateway.
## Removing Entries from an ARP Table
For each device, an ARP cache timer removes ARP entries that have not been used for a specified period of time. The times differ depending on the operating system of the device. For example, newer Windows operating systems store ARP table entries between 15 and 45 seconds, as illustrated in the figure.
## ARP Table on Devices
On a Cisco router, the **show ip arp** command is used to display the ARP table, as shown in the figure.
On a Windows 10 PC, the **arp –a** command is used to display the ARP table, as shown in the figure.
