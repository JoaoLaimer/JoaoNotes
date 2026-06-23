There are five different types of members: Google Accounts, service accounts, Google groups, Google Workspace domains, and Cloud Identity domains.

**Google Account**
A Google Account represents a developer, an administrator, or any other person who interacts with Google Cloud. Any email address that is associated with a Google Account can be an identity, including gmail.com or other domains.

**Service Account**
A service account is an account that belongs to your application instead of to an individual end user. When you run code that is hosted on Google Cloud, you specify the account that the code should run as.

**Google Group**
A Google group is a named collection of Google Accounts and service accounts. Every group has a unique email address that is associated with the group.
You can grant and change access controls for a whole group at once instead of granting or changing access controls one-at-a-time for individual users or service accounts.

**Google Workspace domains**
A Google Workspace domain represents a virtual group of all the Google Accounts that have been created in an organization's Google Workspace account. Google Workspace domains represent your organization's internet domain name, such as example.com, and when you add a user to your Google Workspace domain, a new Google Account is created for the user inside this virtual group, such as username@example.com.

Google Cloud customers who are not Google Workspace customers can get these same capabilities through Cloud Identity.

**Cloud Identity**
Cloud Identity lets you manage users and groups using the Google Admin console, but you do not pay for or receive Google Workspace collaboration products, such as Gmail, Docs, Drive, and Calendar.
You cannot use IAM to create or manage your users or groups. Instead, you can use Cloud Identity or Google Workspace to create and manage users.

## IAM Conditions
Enforce conditional, attribute-based access control for Google Cloud resources.
- Grant resource access to identities (members) only if configured conditions are met.
- Specified in the role binding of a resource's IAM policy.

