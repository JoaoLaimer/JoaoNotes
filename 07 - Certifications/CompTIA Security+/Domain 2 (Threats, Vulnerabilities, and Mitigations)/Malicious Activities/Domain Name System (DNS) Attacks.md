## Domain Name System (DNS)
Responsible for translating human-friendly domain names into IP addresses that computers can understand.
## DNS Cache Poisoning
Involves corrupting the DNS cache data of a DNS resolver with false information.
Utilize DNSSEC to add a digital signature to the organization's DNS data.
## DNS Amplification Attack
The attacker overloads a target system with DNS response traffic by exploiting the DNS resolution process.
Limit the size of DNS responses or rate limit any DNS response traffic.
## DNS Tunneling 
Uses DNS protocol over port 53 to encase non-DNS traffic, trying to evade firewall rules for command control or data exfiltration.
An attacker can use DNS tunneling to evade a company's firewall and steal sensitive data.
## Domain Hijacking
Altering a domain name's registration without the original registrant's consent.
Use domain registry lock services to prevent any unauthorized changes to the domain registrations.
## DNS Zone Transfer Attack
The attacker mimics an authorized system to request and obtain the entire DNS zone data for a domain.

## Pharming Attack
Is a kind os DNS Poisoning attack that happens on the DNS information of the victim's system. 
Exemple: Modified *host* file.
