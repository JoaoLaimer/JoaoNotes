When registering a domain name, entities, must supply identifying information, such as their mailing address, phone number, and email address, to a domain registrar. Anyone can query this information using the `whois` command:
```bash
whois facebook.com
```
This information is not always available, as some organization and individuals use a service called domain privacy, in which a third-party provider replaces the user's information with that of a forwarding service.

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

## Certificate Parsing
Another way of finding hosts is to take advantage of SSL certificates. Use online databases like crt.sh, Censys, and Cert Spotter to find certificates for a domain.
