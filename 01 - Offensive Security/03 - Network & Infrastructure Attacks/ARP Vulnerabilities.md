Any client can send an unsolicited ARP Reply called a “gratuitous ARP.” This is often done when a device first boots up to inform all other devices on the local network of the new device’s MAC address. When a host sends a gratuitous ARP, other hosts on the subnet store the MAC address and IP address contained in the gratuitous ARP in their ARP tables.
## ARP Cache Poisoning
ARP cache poisoning can be used to launch various man-in-the-middle attacks.
When a new host is sending ARP requests a threat actor can respond to these request with it's own IP address in the expected ARP reply for the victim. Doing so the IP address of the threat actor is now in the ARP cache of the victim, the victim can be a router or a PC or both in a man-in-the middle situation.
The ARP poisoning attack can be passive or active. Passive ARP poisoning is where threat actors steal confidential information. Active ARP poisoning is where threat actors modify data in transit, or inject malicious data.
