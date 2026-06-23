**Leverage and understand the resource hierarchy**
- Use projects to group resources that share the same trust boundary.
- Check the policy granted on each resource and make sure you recognize the inheritance.
- Use the principle of least privilege when granting roles.
- Audit policies using Cloud audit logs and audit memberships of groups used in policies.
**Grant roles to Google Groups instead of individuals**
- Update group membership instead of changing an IAM policy.
- Make sure to audit membership of groups used in policies and control the ownership of the Google group used in IAM policies.
- You can also use multiple groups to get better control.
**Service Accounts**
- Be very careful granting `serviceAccountUser` role.
- When you create a service account, give it a display name that clearly identifies its purpose
- Establish a naming convention for service accounts.
- Establish key rotation policies and methods.
- Audit with `serviceAccount.keys.list()` method.
**Identity-Aware Proxy (IAP)**
Enforce access control policies for applications and resources:
- Identity-based access control
- Central authorization layer for application accessed by HTTPS
Iam policy is applied after authentication.
b  