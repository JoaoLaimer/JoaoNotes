## Mandatory Access Control (MAC)
System-enforced access control mechaninsm that's based on subject clearance and the object labels.
## Context-Based Permission
Permission schemes that are defined by various properties for a given file or process.
- AppArmor
## Discretionary Access Control (DAC)
Each object has a list of entities that are allowed to access it.
## SELinux
Default context-based permission scheme that's included inside of CentOS and Red Hat Enterprise Linux.
SELinux enforces MAC on processes and resources and enables information to be classified and protected.
SELinux uses three main contexts:
### User
Defines what users can access an object.
- Unconfined_u (All users)
- User_u (Unprivileged users)
- Sysadmin_u (System Administrators)
- Root (Root user)
### Role
Defines what roles can access a given object
The object_r applies to files and directories.
### Type
Groups objects together that have similar security requirements or characteristics.
## Level
Used to describe the sensitivity level of a given file, directory or process

## Modes
### Disabled
SELinux essentially turned off, and so MAC is not going to be implemented.
### Enforcing
All the SELinux security policies are being enforced.
### Permissive
SELinux is enabled, but the security policies are not enforced.
## Policies Type
- Targeted: process that are targeted are confined in a domain.
- Strict:  every subject and object in the system is enforced to operate on the MAC.
