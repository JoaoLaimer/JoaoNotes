## ICMP Attacks 
Threat actors use ICMP for reconnaissance and scanning attacks. This enables them to launch information-gathering attacks to map out a network topology, discover which hosts are active (reachable), identify the host operating system (OS fingerprinting), and determine the state of a firewall. Threat actors also use ICMP for DoS and DDoS attacks, as shown in the ICMP flood attack.
The following lists common ICMP messages of interest to threat actors:
- **ICMP echo request and echo reply**: This is used to perform host verification and DoS attacks.
- **ICMP unreachable**: This is used to perform network reconnaissance and scanning attacks.
- **ICMP mask reply**: This is used to map an internal IP network.
- **ICMP redirects**: This is used to lure a target host into sending all traffic through a compromised device and create a MiTM attack.
- **ICMP router discovery**: This is used to inject bogus route entries into the routing table of a target host.
Networks should have strict ICMP access control list (ACL) filtering on the network edge to avoid ICMP probing from the internet. Security analysts should be able to detect ICMP-related attacks by looking at captured traffic and log files. In the case of large networks, security devices, such as firewalls and intrusion detection systems (IDS), should detect such attacks and generate alerts to the security analysts.
### Session Hijacking Attack
A **session hijacking attack** is when threat actors gain access to the physical network, and then use an MiTM attack to capture and manipulate traffic, hijacking a legitimate user’s session.
### Amplification and Reflection Attacks
Threat actors often use amplification and reflection techniques to create DoS attacks. 
1. **Amplification -** The treat actor forwords ICMP echo request message to many hosts. These message contain the sourse IP address of the victim.
2. **Reflection -** These hosts all reply to the spoofed IP address of the victim to overwhelm it.
**Note:** Newer forms of amplification and reflection attacks such as DNS-based reflection and amplification attacks and Network Time Protocol (NTP) amplification attacks are now being used.

Threat actors also use resource exhaustion attacks. These attacks consume the resources of a target host to either to crash it or to consume the resources of a network.

### Address Spoofing Attacks
 IP address spoofing attacks occur when a threat actor creates a packet with false source IP address.
 Spoofing attacks can be non-blind or blind:
- **Non-blind spoofing -** The threat actor can see the traffic that is being sent between the host and the target. The threat actor uses non-blind spoofing to inspect the reply packet from the target victim. Non-blind spoofing determines the state of a firewall and sequence-number prediction. It can also hijack an authorized session.
- **Blind spoofing -** The threat actor cannot see the traffic that is being sent between the host and the target. Blind spoofing is used in DoS attacks.