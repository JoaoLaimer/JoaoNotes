This node has many roles, like the Organization Admin. 
The Organization Admin provides a user like Bob, with access to administer all resources belonging to his organization, which is useful for auditing.
There is also a Project Creator role, which allows a user like Alice, to create projects within her organization.

The organization resource is closely associated with a Google Workspace or Cloud Identity Account. When a user with a Google Workspace or Cloud Identity account creates a Google Cloud project, an organization resource is automatically provisioned for them. Then, Google Cloud communicates its availability to the Google Workspace or Cloud Identity super admins. These super admin accounts should be used carefully because they have a lot of control over your organization and all the resources underneath it.

In the context of Google Cloud organization setup, the Google Workspace or Cloud Identity super administrator responsibilities are: Assign the Organization Admin role to some users, be a point of contact in case of recovery issues, and control the lifecycle of the Google Workspace or Cloud Identity account and organization resource.
The responsibilities of the Organization Admin role are: 
- Define IAM policies 
- Determine the structure of the resource hierarchy 
- Delegate responsibility over critical components, such as networking, billing, and resource hierarchy, through IAM roles.


Folders provide an additional grouping mechanism and isolation boundary between projects. Folders can be used to model different legal entities, departments, and teams within a company
Folders allow delegation of administration rights, so for example, each head of a department can be granted full ownership of all Google Cloud resources that belong to their department.

# Resource Manager roles
**Organization**
- **Admin**: Full control over all resources
- **Viewer**: View access to all resources
**Folder**
- Admin: Full control over folders
- Creator: Browse hierarchy and create folders
- Viewer: View folders and projects below a resource
**Project**
- Creator: Create new projects (automatic ownership) and migrate new projects into organization.
- Deleter: Delete projects.
