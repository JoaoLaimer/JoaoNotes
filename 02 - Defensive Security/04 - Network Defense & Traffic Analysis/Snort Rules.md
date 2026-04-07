[[SNORT]] Rules
![[THM Snort Rules IMG.png]]
**Action**:
	- alert, log, drop, reject
	- drop: block and log packet
	- reject: block, log, terminate packet session.
**Protocol**: (IP, TCP, UDP, ICMP)
**IPs**: Range filtering example: 192.168.1.0/24 
	Multiple IPS filtering example: [192.168.1.0, 10.10.10.10, 192.168.1.0/24]
**Ports**: Port range example: 0:8080
	Individual ports example: [21,22,23,24]
**Directions**: arrows: -> <> 
**Rule Options**:

| Rule         | Description                                                                                                                                       |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Msg          | Once rule is triggered, the message filed will appear in the console or log.                                                                      |
| Sid          | Snort rule IDs, each id must be unique.<br>- <100: Reserved<br>- 100-999,999: Rules came with the build.<br>- >=1,000,000: Rules created by user. |
| Reference    | Each rule can have additional information or reference to explain the purpose of the rule or threat pattern. Can be CVE or external info.         |
| Rev          | Revision.                                                                                                                                         |
| Content      | Payload data. Examples: content:"GET", content:"\|47 45 54\|" (hex data)                                                                          |
| Nocase       | Disables case sensitivity.                                                                                                                        |
| Fast_pattern | Prioritise content search to speed up the payload search operation.                                                                               |
| ID           | Filtering the IP id field.                                                                                                                        |
| Flags        | Filtering the TCP Flags.<br>- F - FIN<br>- S - SYN<br>- R - RST<br>- P - PSH<br>- A - ACK<br>- U - URG                                            |
| Dsize        | Filtering the packet payload size.                                                                                                                |
| Sameip       | Filtering the source and destination IP addresses for duplication.                                                                                |
