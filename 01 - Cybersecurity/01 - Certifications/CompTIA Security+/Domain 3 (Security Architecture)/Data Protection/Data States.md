Each state represents a different phase of the data lifecycle, and requires specific security measures to protect against potential threats.
## Data at Rest
Refers to any data stored in databases, file systems, or other storage systems.
#### Protection:
- **Full Disk Encryption** (FDE): Encrypts the entire hard drive.
- **Partition Encryption**: Encrypts specific partitions of a hard drive.
- **File Encryption**: Encrypts individual files.
- **Volume Encryption**: Encrypts a set of selected files or directories.
- **Database Encryption**: Encrypts data stored in a database.
- **Record Encryption**: Encrypts specific fields within a database record.
## Data in Transit/Data in Motion
Refers to data actively moving from one location to another, such as across the Internet or through a private network.
#### Protection:
- **Secure Sockets Layer (SSL) / Transport Layer Security (TLS)**: Cryptographic protocols designed to provide secure communication over a computer network.
- **Virtual Private Network (VPN)**: Technology that creates a secure connection over a less secure network.
- **Internet Protocol Security (IPSec)**: Protocol suite used to secure IP communications by authenticating and encrypting each IP packet in a data stream.
> SSL has been compromised and is not recommended for use.
## Data in Use
Refers to data in the process of being created, retrieved, updated, or deleted.
#### Protection:
- Application Level.
- Access Controls.
- Secure Enclaves.
- Intel Software Guards.