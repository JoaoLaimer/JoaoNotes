## Port
Logical communication endpoint that exists on a computer or server. Ports can any number between 0 and 65,535
### Inbound Port
Logical communication opening on a server that is listening for a connection from a client.
### Outbound Port
Logical communication opening created on a client in order to call out to a server that is listening for a connection.

### Well-Known Ports
Ports 0 to 1023 are considere well-known and are assigned by the Internet Assigned Numbers Authority (IANA).
### Registered Ports
Ports 1024 to 49,151 are considered registered and are usually assigned to proprietary protocols.
### Dynamic and Private ports
Port 49,152 to 65,535 can be used by any application without being registered with IANA.
Commonly used in gaming, instant messaging, and chat for connections.
## Protocol
Rules governing device communication and data exchange.
- Port Number
- Protocol Used
- TCP/UDP support
- Basic description

| Port             | Protocol                                                              | Transport Protocol | Description                                                                                                                                                |
| ---------------- | --------------------------------------------------------------------- | ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 21               | File Transfer Protocol (FTP)                                          | TCP                | Used to transfer files from host to host.                                                                                                                  |
| 22               | Secure Shell (SSH), Secure Copy Protocol (SCP), and Secure FTP (SFTP) | TCP                | Provides secure remote terminal access and file transfer capabilities.<br>Provides secure copy functions.<br>Provides secure file transfers.               |
| 23               | Telnet                                                                | TCP                | Provides insecure remote control of another machine using a text-based environment.                                                                        |
| 24               | Simple Mail Transfer Protocol (SMTP)                                  | TCP                | Provides the ability to send emails over the network.                                                                                                      |
| 53               | Domain Name System (DNS)                                              | UDP, TCP           | Translate domain names into IPs                                                                                                                            |
| 69               | Trivial File Transfer Protocol (TFTP)                                 | UDP                | Used as a lightweight file transfer method for sending configuration files or network booting of an operating system.                                      |
| 80               | Hypertext Transfer Protocol (HTTP)                                    | TCP                | Used for insecure web browsing.                                                                                                                            |
| 88               | Kerberos                                                              | UDP                | Network authentication protocol.                                                                                                                           |
| 110              | Post Office Protocol Version Three (POP3)                             | TCP                | Responsible for retrieving email from a server.                                                                                                            |
| 119              | Network News Transfer Protocol (NNTP)                                 | TCP                | Used for accessing newsgroups                                                                                                                              |
| 135              | Remote Procedure Call (RPC)                                           | TCP and UDP        | Facilitates communication between different system processes.                                                                                              |
| 137, 138 and 139 | NetBIOS                                                               | TCP and UDP        | Networking protocol suite.                                                                                                                                 |
| 143              | Internet Message Access Protocol (IMAP)                               | TCP                | Allows access to email messages on a server.                                                                                                               |
| 161              | Simple Network Management Protocol (SNMP)                             | UDP                | Manages network devices.                                                                                                                                   |
| 162              | SNMP Trap                                                             | UDP                | Responsible for sending SNMP trap messages.                                                                                                                |
| 389              | Lightweight Directory Access Protocol (LDAP)                          | TCP                | Facilitates directory services.                                                                                                                            |
| 443              | HTTP Secure (HTTPS)                                                   | TCP                | Provides secure web communication.                                                                                                                         |
| 445              | Server Message Block (SMB)                                            | TCP                | Used for file and printer sharing over a network.                                                                                                          |
| 465 and 587      | SMTP Secure (SMTPS)                                                   | TCP                | Provides secure SMTP communication.                                                                                                                        |
| 514              | Syslog                                                                | UDP                | Used for sending log messages.                                                                                                                             |
| 636              | LDAP Secure (LDAPS)                                                   | TCP                | LDAP communication over SSL/TLS.                                                                                                                           |
| 993              | Internet Message Access Protocol over SSL/TLS (IMAPS)                 | TCP                | Used for secure email retrieval.                                                                                                                           |
| 995              | Post Office Protocol version 3 over SSL/TLS (POP3S)                   | TCP                | Used for secure email retrieval.                                                                                                                           |
| 1433             | Microsoft SQL                                                         | TCP                | Used to facilitate communication with Microsoft SQL Server.                                                                                                |
| 1645 and 1646    | RADIUS TCP                                                            | TCP                | Used for remote authentication, authorization, and acounting.                                                                                              |
| 1812 and 1813    | RADIUS UDP                                                            | UDP                | Used for authentication and accounting as defined by the internet Engineering Task Force (IETF).                                                           |
| 3389             | Remote Desktop Protocol (RDP)                                         | TCP                | Enables remote desktop access.                                                                                                                             |
| 6514             | Syslog TLS                                                            | TCP                | Used in a secure syslog that uses SSL/TLS to encrypt the IP packets using a certificate before sending them across the IP network to the syslog collector. |
