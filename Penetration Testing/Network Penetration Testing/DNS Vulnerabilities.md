Domain Name Service (DNS) protocol defines an automated service that matches resource names, such as www.cisco.com, with the required numeric network address, such as the IPv4 or IPv6 address. It includes the format for queries, responses, and data and uses resource records (RR) to identify the type of DNS response.

## DNS Open Resolver Attacks
Many organizations use the services of publicly open DNS servers such as GoogleDNS (8.8.8.8) to provide responses to queries. This type of DNS server is called an open resolver. A DNS open resolver answers queries from clients outside of its administrative domain. DNS open resolvers are vulnerable to multiple malicious activities:
#### DNS cache poisoning attacks
Threat actors send spoofed, falsified record resource (RR) information to a DNS resolver to redirect users from legitimate sites to malicious sites. DNS cache poisoning attacks can all be used to inform the DNS resolver to use a malicious name server that is providing RR information for malicious activities.
#### DNS amplification and reflection attacks
Threat actors use DoS or DDoS attacks on DNS open resolvers to increase the volume of attacks and to hide the true source of an attack. Threat actors send DNS messages to the open resolvers using the IP address of a target host. These attacks are possible because the open resolver will respond to queries from anyone asking a question.
#### DNS resource utilization attacks
A DoS attack that consumes the resources of the DNS open resolvers. This DoS attack consumes all the available resources to negatively affect the operations of the DNS open resolver. The impact of this DoS attack may require the DNS open resolver to be rebooted or services to be stopped and restarted.

## DNS Stealth Attacks
To hide their identity, threat actors also use the DNS stealth techniques described in the table to carry out their attacks.
#### Fast Flux
Threat actors use this technique to hide their phishing and malware delivery sites behind a quickly-changing network of compromised DNS hosts. The DNS IP addresses are continuously changed within minutes. Botnets often employ Fast Flux techniques to effectively hide malicious servers from being detected.
#### Double IP Flux
Threat actors use this technique to rapidly change the hostname to IP address mappings and to also change the authoritative name server. This increases the difficulty of identifying the source of the attack.
#### Domain Generation Algorithms
Threat actors use this technique in malware to randomly generate domain names that can then be used as rendezvous points to their command and control (C&C) servers.
### DNS Domain Shadowing Attacks
Domain shadowing involves the threat actor gathering domain account credentials in order to silently create multiple sub-domains to be used during the attacks. These subdomains typically point to malicious servers without alerting the actual owner of the parent domain.
# DNS Tunneling
Threat actors who use DNS tunneling place non-DNS traffic within DNS traffic. This method often circumvents security solutions. For the threat actor to use DNS tunneling, the different types of DNS records such as TXT, MX, SRV, NULL, A, or CNAME are altered. For example, a TXT record can store the commands that are sent to the infected host bots as DNS replies. A DNS tunneling attack using TXT works like this:
1. The data is split into multiple encoded chunks.
2. Each chunk is placed into a lower level domain name label of the DNS query.
3. Because there is no response from the local or networked DNS for the query, the request is sent to the ISP’s recursive DNS servers.
4. The recursive DNS service will forward the query to the attacker’s authoritative name server.
5. The process is repeated until all of the queries containing the chunks are sent.
6. When the attacker’s authoritative name server receives the DNS queries from the infected devices, it sends responses for each DNS query, which contains the encapsulated, encoded commands.
7. The malware on the compromised host recombines the chunks and executes the commands hidden within.
To be able to stop DNS tunneling, a filter that inspects DNS traffic must be used. Pay particular attention to DNS queries that are longer than average, or those that have a suspicious domain name. Also, DNS security solutions, such as Cisco Umbrella (formerly Cisco OpenDNS), block much of the DNS tunneling traffic by identifying suspicious domains.