When registering a domain name, entities, must supply identifying information, such as their mailing address, phone number, and email address, to a domain registrar. Anyone can query this information using the `whois` command:
```bash
whois facebook.com
```
This information is not always available, as some organization and individuals use a service called domain privacy, in which a third-party provider replaces the user's information with that of a forwarding service.

Each WHOIS record typically contains the following information:
- `Domain Name`: The domain name itself (e.g., example.com)
- `Registrar`: The company where the domain was registered (e.g., GoDaddy, Namecheap)
- `Registrant Contact`: The person or organization that registered the domain.
- `Administrative Contact`: The person responsible for managing the domain.
- `Technical Contact`: The person handling technical issues related to the domain.
- `Creation and Expiration Dates`: When the domain was registered and when it's set to expire.
- `Name Servers`: Servers that translate the domain name into an IP address.
## IP Addresses
Another way of discovering a target's top-level domains is to locate IP addresses. Using the tool `nslookup` we can locate an domain name IP.
```bash
nslookup facebook.com
```

Once an IP address is found we can use it to perform a reverse IP lookup. Reverse IP searches look for domains hosted on the same server, given an IP. You can also use **ViewDNS.info** for this. Also run the whois command to an IP address, and then see if the target has a dedicated IP range by checking the NetRange field.
```bash
whois 157.240.2.35
```

Another way of finding IPs is by looking at Autonomous Systems, which are routable networks within the public internet. Autonomous System Numbers (ASNs) identify the owners of these networks.

```bash
whois -h whois.cymru.com 157.240.2.20
```

