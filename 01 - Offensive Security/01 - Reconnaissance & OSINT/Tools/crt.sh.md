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
