A object can be defined as any resource within an AD environment such as OUs, printers, users, domain controlles.

### Users
Users are considered `leaf objects`,which means that they cannot contain any other objects within them. A user object is considered a security principal and has a security identifier (SID) and a global unique identifier (GUID). User objects have many possible [attributes](http://www.kouti.com/tables/userattributes.htm).
### Contacts
A contact object is usually used to represent an external user and contains informational attributes such as first name, last name, email address, telephone number, etc. They are `leaf objects` and are NOT security principals.
### Groups
A group is considered a `container object` because it can contain other objects, including users, computers, and even other groups. A group IS regarded as a security principal and has a SID and a GUID. In AD, groups are a way to manage user permissions and access to other securable objects (both users and computers).

### Organizational Units (OUs)
An organizational unit, or OU from here on out, is a container that systems administrators can use to store similar objects for ease of administration. OUs are often used for administrative delegation of tasks without granting a user account full administrative rights.

### Domain
A domain is the structure of an AD network. Domains contain objects such as users and computers, which are organized into container objects: groups and OUs.
### Domain Controllers
Domain Controllers are essentially the brains of an AD network. They handle authentication requests, verify users on the network, and control who can access the various resources in the domain. All access requests are validated via the domain controller and privileged access requests are based on predetermined roles assigned to users. It also enforces security policies and stores information about every other object in the domain.

#### Sites
A site in AD is a set of computers across one or more subnets connected using high-speed links. They are used to make replication across domain controllers run efficiently.
#### Built-in
In AD, built-in is a container that holds [default groups](https://docs.microsoft.com/en-us/windows/security/identity-protection/access-control/active-directory-security-groups) in an AD domain. They are predefined when an AD domain is created.

#### Foreign Security Principals
A foreign security principal (FSP) is an object created in AD to represent a security principal that belongs to a trusted external forest. They are created when an object such as a user, group, or computer from an external (outside of the current) forest is added to a group in the current domain. They are created automatically after adding a security principal to a group. Every foreign security principal is a placeholder object that holds the SID of the foreign object (an object that belongs to another forest.) Windows uses this SID to resolve the object's name via the trust relationship. FSPs are created in a specific container named ForeignSecurityPrincipals with a distinguished name like `cn=ForeignSecurityPrincipals,dc=inlanefreight,dc=local`.