LDAP, which stands for Lightweight Directory Access Protocol, is a widely used protocol for accessing and maintaining distributed directory information services over an Internet Protocol (IP) network. LDAP enables organizations to manage users centrally, as well as groups and other directory information, often used for authentication and authorization purposes in web and internal applications.
**Services that use LDAP**:
- **Microsoft Active Directory:** A service for Windows domain networks, utilizing LDAP as part of its underlying protocol suite to manage domain resources.
- **OpenLDAP:** An open-source implementation of LDAP, widely used for managing user information and supporting authentication mechanisms across various platforms
### LDIF Format
LDAP entries can be represented usnig LDAP Data Interchange Format (LDIF), a plain text format used to represent LDAP diretories and update operations.
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

