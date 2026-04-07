## Domain Keys Identified Mail (DKIM)
Allows the receiver to check if the email was actually sent by the domain it claims to be sent from and if the content was tampered with during transit.
> DKIM uses a cryptographic signature to verify the authenticity of an email's sender. 
- Email authentication
- Protection against Email Spoofing
- Improved Email Deliverability
- Enhanced Reputation Score
## Sender Policy Framework (SPF)
Email authentication method designed to prevent forging sender addresses during email delivery.
## Domain-based Message Authentication, Reporting & Conformance (DMARC)
An email-validation system designed to detect and prevent email spoofing.
DMARC can work with either DKIM, SPF or both.

## Email Gateway
Server or system that serves as the entry and exit point for emails.
Email gateway routes outgoing email and directs incoming email to user inboxes.
### On-promise Email Gateway
Physical server that is located within an organization's own data center or premises that provides an organization with full control over their email system.
### Cloud-Based Email Gateway
Email gateway that is hosted by third-party cloud service providers to provide greater scalability and ease of maintenance.
### Hybrid Email Gateway
Used to combine the benefits of both on-premise and cloud-based gateways into a single offering.
## Spam Filtering
Process of detecting unwanted an unsolicited emails and preventing them fro reaching a user's email inbox.
- Content analysis
- Bayesian filtering
- DNS-based sinkhole list
- General email filtering rules
## Secure Multipart Internet Message Extensions (S/MIME)
Leverages email certificates to both sign and encrypt email content, ensuring both authenticity and confidentiality.