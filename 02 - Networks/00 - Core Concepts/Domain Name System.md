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
