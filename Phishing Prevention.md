There are various actions a defender can take to help protect the users from falling victim to a malicious email. 

Some examples of these actions are listed below:

- Email Security (SPF, DKIM, DMARC)
- SPAM Filters (flags or blocks incoming emails based on reputation)
- Email Labels (alert users that an incoming email is from an outside source)
- Email Address/Domain/URL Blocking (based on reputation or explicit denylist)
- Attachment Blocking (based on the extension of the attachment)
- Attachment Sandboxing (detonating email attachments in a sandbox environment to detect malicious activity)
- Security Awareness Training (internal phishing campaigns)

Per **MITRE ATT&CK** **Framework**, [Phishing for Information](https://attack.mitre.org/techniques/T1598#mitigations) is described as an attempt to trick targets into divulging information, and contains three sub-techniques.

# **Sender Policy Framework**
Per [dmarcian](https://dmarcian.com/what-is-spf/), "_Sender Policy Framework (SPF) is used to authenticate the sender of an email. With an SPF record in place, Internet Service Providers can verify that a mail server is authorized to send email for a specific domain. An SPF record is a DNS TXT record containing a list of the IP addresses that are allowed to send email on behalf of your domain._"

![[SPF Framework IMG.png]]
**Basic SPF Record**
`v=spf1 ip4:127.0.0.1 include:_spf.google.com -all`

An explanation for the above record:

- `v=spf1` -> This is the start of the SPF record
- `ip4:127.0.0.1` -> This specifies which IP (in this case version IP4 & not IP6) can send mail
- `include:_spf.google.com` -> This specifies which domain can send mail
- `-all` -> non-authorized emails will be rejected
Refer to the SPF Record Syntax on dmarcian [here](https://dmarcian.com/spf-syntax-table/) and [here](https://dmarcian.com/what-is-the-difference-between-spf-all-and-all/).
SPF Surveyor [tool](https://dmarcian.com/spf-survey/).

# **DKIM (DomainKeys Identified Mail)**
Per [dmarcian](https://dmarcian.com/what-is-dkim/), "_DKIM stands for DomainKeys Identified Mail and is used for the authentication of an email that’s being sent. Like SPF, DKIM is an open standard for email authentication that is used for DMARC alignment. A DKIM record exists in the DNS, but it is a bit more complicated than SPF. DKIM’s advantage is that it can survive forwarding, which makes it superior to SPF and a foundation for securing your email._"
How does a DKIM record look like?

`v=DKIM1; k=rsa; p=MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAxTQIC7vZAHHZ7WVv/5x/qH1RAgMQI+y6Xtsn73rWOgeBQjHKbmIEIlgrebyWWFCXjmzIP0NYJrGehenmPWK5bF/TRDstbM8uVQCUWpoRAHzuhIxPSYW6k/w2+HdCECF2gnGmmw1cT6nHjfCyKGsM0On0HDvxP8I5YQIIlzNigP32n1hVnQP+UuInj0wLIdOBIWkHdnFewzGK2+qjF2wmEjx+vqHDnxdUTay5DfTGaqgA9AKjgXNjLEbKlEWvy0tj7UzQRHd24a5+2x/R4Pc7PF/y6OxAwYBZnEPO0sJwio4uqL9CYZcvaHGCLOIMwQmNTPMKGC9nt3PSjujfHUBX3wIDAQAB`

An explanation of the above record:

- `v=DKIM1`-> This is the version of the DKIM record. This is optional. 
- `k=rsa` -> This is the key type. The default value is RSA. RSA is an encryption algorithm (cryptosystem).
- `p=` -> This is the public key that will be matched to the private key, which was created during the DKIM setup process. 

Refer to the DKIM resource [here](https://dmarcian.com/dkim-selectors/) and [here](https://help.returnpath.com/hc/en-us/articles/222481088-DKIM-DNS-record-overview) for additional information.

# **DMARC** 
Per [dmarcian](https://dmarcian.com/start-dmarc/), "_DMARC, (Domain-based  Message Authentication Reporting, & Conformance) an open source standard, uses a concept called alignment to tie the result of two other open source standards, SPF (a published list of servers that are authorized to send email on behalf of a domain) and DKIM (a tamper-evident domain seal associated with a piece of email), to the content of an email. If not already deployed, putting a DMARC record into place for your domain will give you feedback that will allow you to troubleshoot your SPF and DKIM configurations if needed._"

How does a basic DMARC record look like?

`v=DMARC1; p=quarantine; rua=mailto:postmaster@website.com` 

An explanation of the above record:  

- `v=DMARC1` -> Must be in all caps, and it's not optional
- `p=quarantine` -> If a check fails, then an email will be sent to the spam folder (DMARC Policy)
- `rua=mailto:postmaster@website.com` -> Aggregate reports will be sent to this email address

Refer to the DMARC resources [here](https://dmarcian.com/dmarc-record/) and [here](https://dmarc.org/overview/) for additional information on DMARC tags. Review the following resource about DMARC [Alignment](https://dmarcian.com/alignment/).
**Domain Health Checker** from [dmarcian.com](https://dmarcian.com/domain-checker/) to check the DMARC status.

# **S/MIME (Secure/Multipurpose Internet Mail Extensions)**
Per Microsoft, "_S/MIME (Secure/Multipurpose internet Mail Extensions) is a widely accepted protocol for sending digitally signed and encrypted messages_."
Using [Public Key Cryptography](https://www.ibm.com/docs/en/ztpf/2023?topic=concepts-public-key-cryptography), S/MIME guarantees data integrity and nonrepudiation.   

- If Bob wishes to use S/MIME, then he'll need a digital certificate. This digital certificate will contain his public key. 
- With this digital certificate, Bob can "sign" the email message with his private key. 
- Mary can then decrypt Bob's message with Bob's public key. 
- Mary will do the same (send her certificate to Bob) when she replies to his email, and Bob complete the same process on his end.
- Both will now have each other's certificates for future correspondence.
Refer to this Microsoft documentation [here](https://docs.microsoft.com/en-us/exchange/security-and-compliance/smime-exo/smime-exo) for more information on S/MIME and steps on how to configure Office 365 to send/receive S/MIME emails.