AD is a directory service for Windows network environments. It is a distributed, hierarchical structure that allows for centralized management of an organization's resources.
AD provides authentication and authorization functions within a Windows domain environment. 
It is designed to be backward-compatible, and many features are arguably not "secure by default", and it can be easily misconfigured.
Active Directory makes information easy to find and use for administrators and users. AD is highly scalable, supports millions of objects per domain, and allows the creation of additional domains as an organization grows.

AD is essentially a large database accessible to all users within the domain, regardless of their privilege level. A basic AD user account with no added privileges can be used to enumerate the majority of objects contained within AD, including but not limited to:

Domain Computers, Domain Users, Domain Group Information, Organizational Units (OUs), Default Domain Policy, Functional Domain Levels,  Password Policy, Group Policy Objects (GPOs), Domain Trusts, Access Control Lists (ACLs),...

Active Directory is arranged in a hierarchical tree structure, with a forest at the top containing one or more domains, which can themselves have nested subdomains.
A domain is a structure within which contained objects (users, computers, and groups) are accessible. It has many built-in Organizational Units (OUs), such as `Domain Controllers`, `Users`, `Computers`, and new OUs can be created as required. OUs may contain objects and sub-OUs, allowing for the assignment of different group policies. The [[Active Directory Terminology]] is slightly based in OOP terminology.
