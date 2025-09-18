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


## Certificate Transparency Logs
`Certificate Transparency` (`CT`) logs are public, append-only ledgers that record the issuance of SSL/TLS certificates. Whenever a Certificate Authority (CA) issues a new certificate, it must submit it to multiple CT logs. Independent organisations maintain these logs and are open for anyone to inspect.
This transparency serves several crucial purposes:

- Early Detection of Rogue Certificates: By monitoring CT logs, security researchers and website owners can quickly identify suspicious or misused certificates.
- `Accountability for Certificate Authorities`
- `Strengthening the Web PKI (Public Key Infrastructure)`: The Web PKI is the trust system underpinning secure online communication.
## Certificate Parsing
Another way of finding hosts is to take advantage of SSL certificates. Use online databases like crt.sh, Censys, and Cert Spotter to find certificates for a domain.

```shell
 curl -s "https://crt.sh/?q=facebook.com&output=json" | jq -r '.[]
 | select(.name_value | contains("dev")) | .name_value' | sort -u
 
*.dev.facebook.com
*.newdev.facebook.com
*.secure.dev.facebook.com
dev.facebook.com
devvm1958.ftw3.facebook.com
facebook-amex-dev.facebook.com
facebook-amex-sign-enc-dev.facebook.com
newdev.facebook.com
secure.dev.facebook.com
```
