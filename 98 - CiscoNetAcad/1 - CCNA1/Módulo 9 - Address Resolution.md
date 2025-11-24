## 9.1 MAC and IP
### 9.1.1 Destination on Same Network
There are two primary addresses assigned to a device on an Ethernet LAN:
- **Physical address (the MAC address)** - Used for NIC to NIC communications on the same Ethernet network.
- **Logical address (the IP address)** - Used to send the packet from the source device to the destination device. The destination IP address may be on the same IP network as the source or it may be on a remote network.
Layer 2 physical addresses (i.e., Ethernet MAC addresses) are used to deliver the data link frame with the encapsulated IP packet from one NIC to another NIC that is on the same network. If the destination IP address is on the same network, the destination MAC address will be that of the destination device.

### 9.1.2 Destination on Remote Network
When the destination IP address (IPv4 or IPv6) is on a remote network, the destination MAC address will be the address of the host default gateway (i.e., the router interface).
How are the IP addresses of the IP packets in a data flow associated with the MAC addresses on each link along the path to the destination? For IPv4 packets, this is done through a process called Address Resolution Protocol (ARP). For IPv6 packets, the process is ICMPv6 Neighbor Discovery (ND).

## 9.2 ARP
### 9.2.1 ARP Overview
 To send a packet to another host on the same local IPv4 network, a host must know the IPv4 address and the MAC address of the destination device. Device destination IPv4 addresses are either known or resolved by device name. However, MAC addresses must be discovered.
A device uses Address Resolution Protocol (ARP) to determine the destination MAC address of a local device when it knows its IPv4 address.

ARP provides two basic functions:
- Resolving IPv4 addresses to MAC addresses
- Maintaining a table of IPv4 to MAC address mappings
### 9.2.2 ARP Functions
When a packet is sent to the data link layer to be encapsulated into an Ethernet frame, the device refers to a table in its memory to find the MAC address that is mapped to the IPv4 address. This table is stored temporarily in RAM memory and called the ARP table or the ARP cache.
The sending device will search its ARP table for a destination IPv4 address and a corresponding MAC address.

- If the packet’s destination IPv4 address is on the same network as the source IPv4 address, the device will search the ARP table for the destination IPv4 address.
- If the destination IPv4 address is on a different network than the source IPv4 address, the device will search the ARP table for the IPv4 address of the default gateway.
Each entry, or row, of the ARP table binds an IPv4 address with a MAC address. We call the relationship between the two values a map. The ARP table temporarily saves (caches) the mapping for the devices on the LAN.

### 9.2.3 ARP Request
An ARP request is sent when a device needs to determine the MAC address that is associated with an IPv4 address, and it does not have an entry for the IPv4 address in its ARP table.

ARP messages are encapsulated directly within an Ethernet frame. There is no IPv4 header. The ARP request is encapsulated in an Ethernet frame using the following header information:

- **Destination MAC address** - This is a broadcast address FF-FF-FF-FF-FF-FF requiring all Ethernet NICs on the LAN to accept and process the ARP request.
- **Source MAC address** - This is MAC address of the sender of the ARP request.
- **Type** - ARP messages have a type field of 0x806. This informs the receiving NIC that the data portion of the frame needs to be passed to the ARP process. A router will not forward broadcasts out other interfaces.
### 9.2.4 ARP Reply
Only the device with the target IPv4 address associated with the ARP request will respond with an ARP reply. The ARP reply is encapsulated in an Ethernet frame using the following header information:

- **Destination MAC address** - This is the MAC address of the sender of the ARP request.
- **Source MAC address** - This is the MAC address of the sender of the ARP reply.
- **Type** - ARP messages have a type field of 0x806. This informs the receiving NIC that the data portion of the frame needs to be passed to the ARP process.
Only the device that originally sent the ARP request will receive the unicast ARP reply. After the ARP reply is received, the device will add the IPv4 address and the corresponding MAC address to its ARP table. Packets destined for that IPv4 address can now be encapsulated in frames using its corresponding MAC address.

If no device responds to the ARP request, the packet is dropped because a frame cannot be created.

Entries in the ARP table are time stamped.

Additionally, static map entries can be entered in an ARP table, but this is rarely done. Static ARP table entries do not expire over time and must be manually removed.

**Note:** IPv6 uses a similar process to ARP for IPv4, known as ICMPv6 Neighbor Discovery (ND). IPv6 uses neighbor solicitation and neighbor advertisement messages, similar to IPv4 ARP requests and ARP replies.

### 9.2.5 ARP Role in Remote Communications
When the destination IPv4 address is not on the same network as the source IPv4 address, the source device needs to send the frame to its default gateway. Whenever a source device has a packet with an IPv4 address on another network, it will encapsulate that packet in a frame using the destination MAC address of the router.

The IPv4 address of the default gateway is stored in the IPv4 configuration of the hosts. When a host creates a packet for a destination, it compares the destination IPv4 address and its own IPv4 address to determine if the two IPv4 addresses are located on the same Layer 3 network. If the destination host is not on its same network, the source checks its ARP table for an entry with the IPv4 address of the default gateway. If there is not an entry, it uses the ARP process to determine a MAC address of the default gateway.

### 9.2.6 Removing Entries from an ARP Table
For each device, an ARP cache timer removes ARP entries that have not been used for a specified period of time. The times differ depending on the operating system of the device. For example, newer Windows operating systems store ARP table entries between 15 and 45 seconds.

### 9.2.7 ARP Tables on Networking Devices
On a Cisco router, the **show ip arp** command is used to display the ARP table:
```
R1# show ip arp 
Protocol  Address          Age (min)  Hardware Addr   Type   Interface
Internet  192.168.10.1            -   a0e0.af0d.e140  ARPA   GigabitEthernet0/0/0
Internet  209.165.200.225         -   a0e0.af0d.e141  ARPA   GigabitEthernet0/0/1
Internet  209.165.200.226         1   a03d.6fe1.9d91  ARPA   GigabitEthernet0/0/1

R1#
```

On a Windows 10 PC, the **arp -a** command is used to display the ARP table:
```
C:\Users\PC> arp -a
Interface: 192.168.1.124 --- 0x10
  Internet Address      Physical Address      Type
  192.168.1.1           c8-d7-19-cc-a0-86     dynamic
  192.168.1.101         08-3e-0c-f5-f7-77     dynamic
  192.168.1.110         08-3e-0c-f5-f7-56     dynamic  
  192.168.1.112         ac-b3-13-4a-bd-d0     dynamic  
  192.168.1.117         08-3e-0c-f5-f7-5c     dynamic  
  192.168.1.126         24-77-03-45-5d-c4     dynamic  
  192.168.1.146         94-57-a5-0c-5b-02     dynamic  
  192.168.1.255         ff-ff-ff-ff-ff-ff     static  
  224.0.0.22            01-00-5e-00-00-16     static  
  224.0.0.251           01-00-5e-00-00-fb     static  
  239.255.255.250       01-00-5e-7f-ff-fa     static  
  255.255.255.255       ff-ff-ff-ff-ff-ff     static
C:\Users\PC>
```

### 9.2.8 ARP Issues - ARP Broadcasts and ARP Spoofing
If a large number of devices were to be powered up and all start accessing network services at the same time, there could be some reduction in performance for a short period of time,

A threat actor can use ARP spoofing to perform an ARP poisoning attack. This is a technique used by a threat actor to reply to an ARP request for an IPv4 address that belongs to another device, such as the default gateway.

Enterprise level switches include mitigation techniques known as dynamic ARP inspection (DAI).
## 9.3 IPv6 Neighbor Discovery
### 9.3.2 IPv6 Neighbor Discovery Messages
IPv6 Neighbor Discovery protocol is sometimes referred to as ND or NDP.

ND provides address resolution, router discovery, and redirection services for IPv6 using ICMPv6. ICMPv6 ND uses five ICMPv6 messages to perform these services:

- Neighbor Solicitation messages
- Neighbor Advertisement messages
- Router Solicitation messages
- Router Advertisement messages
- Redirect Message

Neighbor Solicitation and Neighbor Advertisement messages are used for device-to-device messaging such as address resolution (similar to ARP for IPv4). Devices include both host computers and routers.
Router Solicitation and Router Advertisement messages are for messaging between devices and routers. Typically router discovery is used for dynamic address allocation and stateless address autoconfiguration (SLAAC).

**Note:** The fifth ICMPv6 ND message is a redirect message which is used for better next-hop selection. This is beyond the scope of this course.

IPv6 ND is defined in the IETF RFC 4861.

ND messages are multicast.
### 9.3.3 IPv6 Neighbor Discovery - Address Resolution
ICMPv6 Neighbor Solicitation and Neighbor Advertisement messages are used for MAC address resolution. This is similar to ARP Requests and ARP Replies used by ARP for IPv4. For example, assume PC1 wants to ping PC2 at IPv6 address 2001:db8:acad:: 11. To determine the MAC address for the known IPv6 address, PC1 sends an ICMPv6 Neighbor Solicitation message.
**ICMPv6 Neighbor Solicitation Message**  
_"Hey whoever has 2001:db8:acad:1::11, send me your MAC address?"_

The solicited IPv6 is encapsulated in a ICMPv6 NS, this IP is then mapped to a solicited-node multicast address, that is then mapped to a multicast MAC IPV6 address.
Example: 
- Destination IPV6: 2001:db8:acad:1:: 11  -> take last 24 bits: 00:0011
- SN-Multicast Address: ff02::1:ff**00:0011**
- MAC Multicast Address: 33:33:ff:**00:00:11**

**ICMPv6 Neighbor Advertisement Message**  
_"Hey 2001:db8:acad:1:: 10, I am 2001:db8:acad:1:: 11 and my MAC address is f8-94-c3-e4-c5-0A."_

ICMPv6 Neighbor Solicitation messages are sent using special Ethernet and IPv6 multicast addresses. This allows the Ethernet NIC of the receiving device to determine whether the Neighbor Solicitation message is for itself without having to send it to the operating system for processing.