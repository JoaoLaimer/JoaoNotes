Used to translate IP addresses into human readable names.
On the internet, fully-qualified domain names (FQDNs), like google.com, are much easier for people to remember than 142.250.219.206, which is the actual numeric address for this server.
If google decides to change the numerical address, the new address is simply linked to the existing domain name.
The DNS protocol communications use a single messages, and the transfer of resource record information between servers.
1. The user types an FQDN into a browser application.
2. A DNS query is sent to the designated DNS server for the client computer.
3. The DNS server matches the FQDN with its IP address.
4. The DNS query response is sent back to the client with the IP address for the FQDN.
5. The client computer uses the IP address to make requests of the server.
## DNS Message Format
The DNS server stores different types of records used to resolve names:
- **A** - An end device IPv4 address.
- **NS** - An authoritative name server.
- **AAAA** - An end device IPv6 address (pronounced quad-A).
- **MX** - A mail exchange record.
The DNS client service on Windows PCs also stores previously resolved names in memory. The `ipconfig /displaydns` command displays all of the cached DNS entries.
DNS uses the same message format between servers, consisting of a question, answer, authority, and additional information for all types of client queries and server responses, error messages, and transfer of resource record information.
- **Question**: The question for the name server.
- **Answer**: Resource Records answering the question.
- **Authority**: Resource Records pointing toward an authority.
- **Additional**: Resource Records holding additional information.
## DNS Hierarchy
The DNS protocol uses a hierarchical system to create a database to provide name resolution.
Each DNS server maintains a specific database file and is only responsible for managing name-to-IP mappings for that small portion of the entire DNS structure.
When a DNS server receives a request for a name translation that is not within its DNS zone, the DNS server forwards the request to another DNS server within the proper zone for translation.
Top-Level domains represent either the type of organization or the country of origin:
- **.com** - a business or industry
- **.org** - a non-profit organization
- **.au** - Australia
- **.co** - Colombia

|DNS Concept|Description|Example|
|---|---|---|
|`Domain Name`|A human-readable label for a website or other internet resource.|`www.example.com`|
|`IP Address`|A unique numerical identifier assigned to each device connected to the internet.|`192.0.2.1`|
|`DNS Resolver`|A server that translates domain names into IP addresses.|Your ISP's DNS server or public resolvers like Google DNS (`8.8.8.8`)|
|`Root Name Server`|The top-level servers in the DNS hierarchy.|There are 13 root servers worldwide, named A-M: `a.root-servers.net`|
|`TLD Name Server`|Servers responsible for specific top-level domains (e.g., .com, .org).|[Verisign](https://en.wikipedia.org/wiki/Verisign) for `.com`, [PIR](https://en.wikipedia.org/wiki/Public_Interest_Registry) for `.org`|
|`Authoritative Name Server`|The server that holds the actual IP address for a domain.|Often managed by hosting providers or domain registrars.|
|`DNS Record Types`|Different types of information stored in DNS.|A, AAAA, CNAME, MX, NS, TXT, etc.|

| Record Type | Full Name                 | Description                                                                                                                                 | Zone File Example                                                                              |
| ----------- | ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `A`         | Address Record            | Maps a hostname to its IPv4 address.                                                                                                        | `www.example.com.` IN A `192.0.2.1`                                                            |
| `AAAA`      | IPv6 Address Record       | Maps a hostname to its IPv6 address.                                                                                                        | `www.example.com.` IN AAAA `2001:db8:85a3::8a2e:370:7334`                                      |
| `CNAME`     | Canonical Name Record     | Creates an alias for a hostname, pointing it to another hostname.                                                                           | `blog.example.com.` IN CNAME `webserver.example.net.`                                          |
| `MX`        | Mail Exchange Record      | Specifies the mail server(s) responsible for handling email for the domain.                                                                 | `example.com.` IN MX 10 `mail.example.com.`                                                    |
| `NS`        | Name Server Record        | Delegates a DNS zone to a specific authoritative name server.                                                                               | `example.com.` IN NS `ns1.example.com.`                                                        |
| `TXT`       | Text Record               | Stores arbitrary text information, often used for domain verification or security policies.                                                 | `example.com.` IN TXT `"v=spf1 mx -all"` (SPF record)                                          |
| `SOA`       | Start of Authority Record | Specifies administrative information about a DNS zone, including the primary name server, responsible person's email, and other parameters. | `example.com.` IN SOA `ns1.example.com. admin.example.com. 2024060301 10800 3600 604800 86400` |
| `SRV`       | Service Record            | Defines the hostname and port number for specific services.                                                                                 | `_sip._udp.example.com.` IN SRV 10 5 5060 `sipserver.example.com.`                             |
| `PTR`       | Pointer Record            | Used for reverse DNS lookups, mapping an IP address to a hostname.                                                                          | `1.2.0.192.in-addr.arpa.` IN PTR `www.example.com.`                                            |