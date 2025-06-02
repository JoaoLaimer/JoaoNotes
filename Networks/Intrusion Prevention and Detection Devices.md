#### **Common Characteristics of IDS and IPS**
- Both technologies are deployed as sensors.
- Both technologies use signature to detect patterns of misuse in network traffic.
- Both can detect atomic patterns (single-packet) or composite patterns (multi-packet).
- IDS and IPS technologies use signatures to detect patterns in network traffic. A signature is a set of rules that an IDS or IPS uses to detect malicious activity. Signatures can be used to detect severe breaches of security, to detect common network attacks, and to gather information.
### Advantages and Disadvantages

| Solution | Advantages                                                                                                                  | Disadvantages                                                                                                                                               |
| -------- | --------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| IDS      | - No impact on network (latency, jitter)<br>- No network impact if sensor failure<br>- No network impact if sensor overload | - Response action cannot stop trigger packets<br>- Correct tuning required for response actions<br>- More vulnerable to network security evasion techniques |
| IPS      | - Stop trigger packets<br>- Can use stream normalization techniques                                                         | - Sensor issues might affect network traffic<br>- Sensor overloading impacts the network<br>- Some impact on network (latency, jitter)                      |
You can deploy both an IPS and an IDS. Using one of these technologies does not negate the use of the other. In fact, IDS and IPS technologies can complement each other.

For example, an IDS can be implemented to validate IPS operation because the IDS can be configured for deeper packet inspection offline. This allows the IPS to focus on fewer but more critical traffic patterns inline.

Deciding which implementation to use is based on the security goals of the organization as stated in their network security policy.

## Types of IPS
### Host-based IPS
Or HIPS is software installed on a host to monitor and analyze suspicious activity. HIPS can be thought of as a combination of antivirus software, antimalware software, and a firewall. Combined with a network-based IPS, HIPS is an effective tool in providing additional protection for the host.
### Network-based IPS
network-based IPS can be implemented using a dedicated or non-dedicated IPS device. Network-based IPS implementations are a critical component of intrusion prevention. There are host-based IDS/IPS solutions, but these must be integrated with a network-based IPS implementation to ensure a robust security architecture.
Sensors detect malicious and unauthorized activity in real time and can take action when required.