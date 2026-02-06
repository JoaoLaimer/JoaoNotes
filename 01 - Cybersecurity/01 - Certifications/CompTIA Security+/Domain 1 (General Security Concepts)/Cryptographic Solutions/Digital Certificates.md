Digitally signed electronic document that binds a public key with a user's identity.
## Wildcard Certificate
Allows all of the subdomains to use the same public key certificate and have it displayed as valid.
- Easier to maintain.
- Revoking it makes so it affects all sub-domains.
### Subject Alternate Name (SAN)
Certificate that specifies what additional domain and IP addresses are going to be supported.
## Single-Sided Certificate
Only requires the server to be validated.
## Dual-Sided Certificate
Requires both the server and the user to be validated.
## Self-Signed Certificate
Digital certificate that is signed by the same entity whose identity it certifies.
- Less trustful.
- Used for test environment.
## Third-Party Certificate
Digital certificate issued and signed by a trusted certificate authority (CA).
- Preferred choice.
## Root of Trust
Each certificate is validated using the concept of a root of trust or the chain of trust.
The root is usually a trusted third-party provider like:
- Verisign 
- Google 
- Amazon
- CloudFlare
## Certificate Authority
Trusted third party who is going to issue these digital certificates.
## Registration Authority
Requests identifying information from the user and forwards that certificate request up to the certificate authority to create the digital certificate.
## Certificate Signing Request (CSR)
A block of encoded text that contains information about the entity requesting the certificate.
## Certificate Revocation List (CRL)
Server as an online list of digital certificates that the certificate authority has already revoked.
## OCSP (Online Certificate Status Protocol)
Allows to determine the revocation status of any digital certificate using its serial number or name.
## OCSP Stapling
Allows the certificate holder to get the OCSP record from the server at regular intervals.
## Public Key Pinning 
Allows an HTTPS website to resist impersonation attacks from users who are trying to present fraudulent certificates by presenting a set of trusted public keys to the user's web browser HTTP header.
If the browser doesn't get the matching public key from the certificate authority, then it knows that the website was compromised and it's going to alert the user that there is an issue.
## Key Escrow Agents
Occurs when a secure copy of a user's private key is being held just in case the user lose access to the private key.
## Key Recovery Agent
Specialized type of software that allows the restoration of a lost or corrupted key to be performed.
