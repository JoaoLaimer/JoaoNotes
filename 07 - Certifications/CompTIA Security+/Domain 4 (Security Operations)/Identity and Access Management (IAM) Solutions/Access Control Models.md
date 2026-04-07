## Mandatory Access Control (MAC)
Employs security labels to authorize user access to specific resources.
In MAC, if not explicitly allowed, it's considered forbidden for users.
> The MAC scheme uses sensitivity labels for users and data. It is commonly used when access needs to be restricted based on a need to know. Sensitivity labels often reflect classification levels of data and clearances granted to individuals.
## Discretionary Access Control (DAC)
Resource's owner determines which users can access each resource.
>The DAC scheme specifies that every object has an owner, and the owner has full, explicit control of the object. Microsoft NTFS uses the DAC scheme.
## Role-Based Access Control (RBAC)
Assign users to roles and uses these roles to grant permissions to resources.
Role-based access control enforces minimum privileges.
## Rule-Based Access Control (RBAC)
Enables administrators to apply security policies to all users.
> Remember: conditionality. 
> Rule-based access control is based on a set of approved instructions, such as an access control list. Some rule-BAC systems use rules that trigger in response to an event, such as modifying ACLs after detecting an attack or granting additional permissions to a user in certain situations.
## Attribute-based Access Control (ABAC)
Uses object characteristics for access control decisions.
**User Attributes**: User's name, role, organization, ID, or security clearance level.
**Environment Attributes**: Time of access, data location, and current organization's threat level.
**Resource Attributes**: File creation date, resource owner, file name, and data sensitivity.
> It evaluates multiple attributes from a single object.

> The ABAC scheme uses attributes defined in policies to grant access to resources. It's commonly used in software-defined networks (SDNs).

## Time of Day Restrictions
Controls restrict resource access based on request times.
## Principle of Least Privilege
Granting users the minimum access required for their tasks without extra privileges.
Least privilege reduces the risk of an account being misused if compromised by an threat actor.
Least privilege requires continually reviewing user permissions to prevent permission creep.
## Permission or Authorization Creep
Occurs when a user gains excessive rights during their career progression in the company.
## Just-in-Time Permissions
By granting access only when it's specifically needed and for a short duration, just-in-time permissions minimize the exposure of critical systems.
## Ephemeral credentials
Ephemeral credentials are temporary and designed for short-lived purposes, thus reducing the risk of those credentials being misused or compromised.

>A role-based access control scheme uses roles based on jobs and functions. A roles and permissions matrix is a planning document that matches the roles with the required privileges.