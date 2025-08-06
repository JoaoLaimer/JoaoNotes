## Socket Pair
The socket is used to identify the server and service being requested by the client. A client socket might look like this, with 1099 representing the source port number: 192.168.1.5:1099
The socket on a web server might be 192.168.1.7:80
Together, these two sockets combine to form a _socket pair_: 192.168.1.5:1099, 192.168.1.7:80
Sockets enable multiple processes, running on a client, to distinguish themselves from each other, and multiple connections to a server process to be distinguished from each other.

## Port Number Groups
The IANA is the standards organization responsible for assigning various addressing standards, including the 16-bit port numbers. The 16 bits used to identify the source and destination port numbers provides a range of ports from 0 through 65535.

| Port Group                   | Number Range   | Description                                                                                                                                                                                                                                                        |
| ---------------------------- | -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Well-known Ports             | 0 to 1023      | These ports are reserved for common or popular services and applicaiton such as web browsers, email clients, and remote access clients. Defined wll-known ports for common server applications enables clients to easily identify the associated service required. |
| Registered Ports             | 1024 to 49151  | Assigned by IANA to a requesting entity to use with specific processes or application. These processes are primarily individual applications that a user has chosen to install, rather than common application that would receive a well-known port number.        |
| Private and/or Dynamic Ports | 49152 to 65535 | A.k.a ephemeral ports, the client's OS usually assign port numbers dynamically when a connection to a service is initiated. The dynamic port is then used to identify the client application during communication.                                                 |

### Well-known Ports Group

| Port Number | Protocol | Application                                         |
| ----------- | -------- | --------------------------------------------------- |
| 20          | TCP      | File Transfer Protocol (FTP) - Data                 |
| 21          | TCP      | File Transfer Protocol (FTP) - Control              |
| 22          | TCP      | Secure Shell (SSH)                                  |
| 23          | TCP      | Telnet                                              |
| 25          | TCP      | Simple Mail Transfer Protocol (SMTP)                |
| 53          | UDP,TCP  | Domain Name Service (DNS)                           |
| 67          | UDP      | Dynamic Host Configuration Protocol (DHCP) - Server |
| 68          | UDP      | Dynamic Host Configuration Protocol - Client        |
| 69          | UDP      | Trivial File Transfer Protocol (TFTP)               |
| 80          | TCP      | HyperText Transfer Protocol (HTTP)                  |
| 110         | TCP      | Post Office Protocol version 3 (POP3)               |
| 143         | TCP      | Internet Message Access Protocol (IMAP)             |
| 161         | UDP      | Simple Network Management Protocol (SNMP)           |
| 443         | TCP      | Hypertext Transfer Protocol Secure (HTTPS)          |
