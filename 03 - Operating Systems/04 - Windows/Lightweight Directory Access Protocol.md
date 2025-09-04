LDAP, which stands for Lightweight Directory Access Protocol, is a widely used protocol for accessing and maintaining distributed directory information services over an Internet Protocol (IP) network. LDAP enables organizations to manage users centrally, as well as groups and other directory information, often used for authentication and authorization purposes in web and internal applications.
**Services that use LDAP**:
- **Microsoft Active Directory:** A service for Windows domain networks, utilizing LDAP as part of its underlying protocol suite to manage domain resources.
- **OpenLDAP:** An open-source implementation of LDAP, widely used for managing user information and supporting authentication mechanisms across various platforms
The latest LDAP specification is [Version 3](https://tools.ietf.org/html/rfc4511), published as RFC 4511. A firm understanding of how LDAP works in an [[Active Directory]] environment is crucial for attackers and defenders. LDAP uses port 389, and LDAP over SSL (LDAPS) communicates over port 636.
### LDIF Format
LDAP entries can be represented using LDAP Data Interchange Format (LDIF), a plain text format used to represent LDAP diretories and update operations.
### Structure
An LDAP directory follows a hierarchical structure like a file system's tree.
At the top of the LDAP tree, we find the top-level domain (TLD), such as `dc=ldap, dc=joao`. Beneath the TLD, there may be subdomain or organizational units (OUs), such as `ou=people`, which further categorize the directory entries.
- **Distinguished Names (DNs)**: Serve as unique identifiers for each entry in the directory, specifiying the path from the top of the LDAP tree to the entry.
- **Relative Distinguished Names (RDNs)**: Represent individual levels within the directory hierarchy, such as `cn=joao vitor`, where `cn` stands for common name.
- **Attributes**: Define the properties of directory entries, like `mail=email@email.com`.
## Search Queries
An LDAP query consists of several components:
1. **Base DN (Distinguished Name):** This is the search's starting point in the directory tree.
2. **Scope**: Defines how deep the search should go from the base DN:
- `base` - search the base DN only;
- `one` - search the immediate children of the base DN;
- `sub` - search the base DN and all its descendants.
3. **Filter**: A match to be returned in the search results.
4. **Attributes**: Specifies which characteristics of the matching entries should be returned in the search results.

```
(base DN) (scope) (filter) (attibutes)
```
#### Filters and Syntax
The syntax for LDAP filters is defined in [RFC 4515](https://www.openldap.org/lists/ietf-ldapbis/200606/msg00010.html), where filters are represented as strings with a specific format, such as `(canonicalName=value)`. LDAP filters can use a variety of operators to refine search criteria, including equality (`=`), presence (`=*`), greater than (`>=`), and less than (`<=`).
Example: `(cn=John Doe)` - This filters targets canonical names matching "John Doe".
`(&(objectClass=user)(|(cn=John*)(cn=Jane*)))` - This filter searches for entries classified as "user" in their object class with a canonical name starting with either "John" or "Jane".

While not commonly exposed directly, LDAP services can be accessible over the network via ports 389 (for unencrypted or StartTLS connections) and 636 (for SSL/TLS connections). When LDAP services are accessible publicly, tools such as `ldapsearch`, part of the OpenLDAP suite, can be used to interact with the LDAP server.

#### AD LDAP Authentication

LDAP is set up to authenticate credentials against AD using a "BIND" operation to set the authentication state for an LDAP session. There are two types of LDAP authentication.

1. `Simple Authentication`: This includes anonymous authentication, unauthenticated authentication, and username/password authentication. Simple authentication means that a `username` and `password` create a BIND request to authenticate to the LDAP server.
    
2. `SASL Authentication`: [The Simple Authentication and Security Layer (SASL)](https://en.wikipedia.org/wiki/Simple_Authentication_and_Security_Layer) framework uses other authentication services, such as Kerberos, to bind to the LDAP server and then uses this authentication service (Kerberos in this example) to authenticate to LDAP. The LDAP server uses the LDAP protocol to send an LDAP message to the authorization service, which initiates a series of challenge/response messages resulting in either successful or unsuccessful authentication. SASL can provide additional security due to the separation of authentication methods from application protocols.
    

LDAP authentication messages are sent in cleartext by default so anyone can sniff out LDAP messages on the internal network. It is recommended to use TLS encryption or similar to safeguard this information in transit.