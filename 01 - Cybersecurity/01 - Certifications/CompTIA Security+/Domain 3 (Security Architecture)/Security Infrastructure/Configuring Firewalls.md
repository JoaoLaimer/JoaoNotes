## Access Control List (ACL)
A rule set that is placed on firewalls, routers, and other network infrastructure devices that permit or allow traffic through a particular interface.

Rules are applied at a top-down approach.
Include a deny all rule at the end  of the ACL.
- Web-Based Interface
- Command-Line Interface 

Rules are made up with:
- Type
- Source
- Destination
- Action
> Firewalls use a deny any any, deny any, or a drop all statement at the end of the ACL to enforce an implicit deny strategy. The statement forces the firewall to block any traffic that wasn't previously allowed in the ACL. The implicit deny strategy provides a secure starting point for a firewall.
- 