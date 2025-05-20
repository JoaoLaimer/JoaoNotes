## TCP Header Values
![[TCPHeaderIMG.png]]
## TCP SYN Flood Attack
The TCP SYN Flood attack exploits the TCP three-way handshake. The figure shows a threat actor continually sending TCP SYN session request packets with a randomly spoofed source IP address to a target. The target device replies with a TCP SYN-ACK packet to the spoofed IP address and waits for a TCP ACK packet. Those responses never arrive. Eventually the target host is overwhelmed with half-open TCP connections, and TCP services are denied to legitimate users.
1. The treat actor sends multiple SYN requests to the web server.
2. The web server replies with SYN-ACK's for each SYN request and wait for to complete the three way handshake.The treat actor does not respond to the SYN-ACK's.
3. The valid user cannot acess the web server beacuse the web server has too many half-opened TCP connections.
## TCP Reset Attack
A TCP reset attack can be used to terminate TCP communications between two hosts. The figure displays how TCP uses a four-way exchange to close the TCP connection using a pair of FIN and ACK segments from each TCP endpoint. A TCP connection terminates when it receives an RST bit. This is an abrupt way to tear down the TCP connection and inform the receiving host to immediately stop using the TCP connection. A threat actor could do a TCP reset attack and send a spoofed packet containing a TCP RST to one or both endpoints.
## TCP Session Hijacking
TCP session hijacking is another TCP vulnerability. Although difficult to conduct, a threat actor takes over an already-authenticated host as it communicates with the target. The threat actor must spoof the IP address of one host, predict the next sequence number, and send an ACK to the other host. If successful, the threat actor could send, but not receive, data from the target device.
## UDP Header Values
![[UDPHeaderIMG.png]]
## UDP Flood Attacks
You are more likely to see a UDP flood attack. In a UDP flood attack, all the resources on a network are consumed. The threat actor must use a tool like UDP Unicorn or Low Orbit Ion Cannon. These tools send a flood of UDP packets, often from a spoofed host, to a server on the subnet. The program will sweep through all the known ports trying to find closed ports. This will cause the server to reply with an ICMP port unreachable message. Because there are many closed ports on the server, this creates a lot of traffic on the segment, which uses up most of the bandwidth. The result is very similar to a DoS attack.