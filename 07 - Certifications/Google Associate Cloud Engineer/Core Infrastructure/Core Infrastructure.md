# Google Cloud Network
Google Cloud’s infrastructure is based in seven major geographic locations: North America, South America, Europe, Africa, the Middle East, Asia, and Australia.

Each of these locations is divided into several different regions and zones. Regions represent independent geographic areas and are composed of zones.
For example, London, or europe-west2, is a region that currently comprises three different zones. A zone is an area where Google Cloud resources are deployed. 
For example, if you launch a virtual machine using Compute Engine it will run in the zone that you specify to ensure resource redundancy.

Some of Google Cloud’s services support placing resources in what we call a multi-region. For example, Spanner multi-region configurations allow you to replicate the database's data not just in multiple zones, but in multiple zones across multiple regions, as defined by the instance configuration.
# Environment Impact
Google's data centers were the first to achieve ISO 14001 certification, which is a standard that maps out a framework for an organization to enhance its environmental performance through improving resource efficiency and reducing waste.
In their founding decade, Google became the first major company to be carbon neutral.
In their second decade, we were the first company to achieve 100% renewable energy.
By 2030, they aim to be the first major company to operate completely carbon free.
# Security
The security infrastructure can be explained in progressive layers, starting from the physical security of our data centers, continuing on to how the hardware and software that underlie the infrastructure are secured, and finally, describing the technical constraints and processes in place to support operational security.

We begin with the Hardware infrastructure layer which comprises three key security features: The first is hardware design and provenance. Both the server boards and the networking equipment in Google data centers are custom-designed by Google.
Google also designs custom chips, including a hardware security chip that's currently being deployed on both servers and peripherals.

The next feature is a secure boot stack. Google server machines use a variety of technologies to ensure that they are booting the correct software stack, such as cryptographic signatures over the BIOS, bootloader, kernel, and base operating system image.

This layer's final feature is premises security. Google designs and builds its own data centers, which incorporate multiple layers of physical security protections. Access to these data centers is limited to only a very small number of Google employees. Google additionally hosts some servers in third-party data centers, where we ensure that there are Google-controlled physical security measures on top of the security layers provided by the data center operator.

Next is the Service deployment layer, where the key feature is encryption of inter-service communication. Google’s infrastructure provides cryptographic privacy and integrity for remote procedure call (“RPC”) data on the network. Google’s services communicate with each other using RPC calls. The infrastructure automatically encrypts all infrastructure RPC traffic that goes between data centers. Google has started to deploy hardware cryptographic accelerators that will allow it to extend this default encryption to all infrastructure RPC traffic inside Google data centers.

Google’s central identity service, which usually manifests to end users as the Google login page, goes beyond asking for a simple username and password. 
On the Storage services layer we find the encryption at rest security feature. Most applications at Google access physical storage (in other words, “file storage”) indirectly via storage services, and encryption using centrally managed keys is applied at the layer of these storage services. Google also enables hardware encryption support in hard drives and SSDs.

The final layer is Google's Operational security layer which provides four key features.
First is intrusion detection.
Google conducts Red Team exercises to measure and improve the effectiveness of its detection and response mechanisms.
Next is reducing insider risk.
Then there’s employee U2F use.
Finally, there are stringent software development practices.

# Open Source Ecosystems
Google publishes key elements of technology using open source licenses to create ecosystems that provide customers with options other than Google.
Kubernetes and Google Kubernetes Engine give customers the ability to mix and match microservices running across different clouds, while Google Cloud Observability lets customers monitor workloads across multiple cloud providers.

# Pricing and Billing
Same as AWS but they really want to show that they developed "by second billing".

# Resource Hierarchy
1. Resources: These represent virtual machines, Cloud Storage buckets, tables in BigQuery, or anything else in Google Cloud.
2. Projects: Resources are organized into projects. 
3. Folders: Projects can be organized into folders.
4. Organization: Encompasses all the projects, folders, and resources in your organization.
## Projects
Projects are the basis for enabling and using Google Cloud services, like managing APIs, enabling billing, adding and removing collaborators, and enabling other Google services. Projects can have different owners and users because they’re billed and managed separately. Each Google Cloud project has three identifying attributes: a project ID, a project name, and a project number. 
The project ID is a globally unique identifier assigned by Google that can’t be changed after creation.
Project IDs are used in different contexts to inform Google Cloud of the exact project to work with.

| Project ID                                            | Project Name        | Project Number            |
| ----------------------------------------------------- | ------------------- | ------------------------- |
| Globally unique.                                      | Need not be unique. | Globally unique.          |
| Assigned by Google Cloud but mutable during creation. | Chosen by you.      | Assigned by Google Cloud. |
| Immutable after creation.                             | Mutable.            | Immutable.                |

Google Cloud’s Resource Manager tool is designed to programmatically help you manage projects. It’s an API that can gather a list of all the projects associated with an account, create new projects, update existing projects, and delete projects. It can even recover projects that were previously deleted,and can be accessed through the RPC API and the REST API.

## Folders
Folders let you assign policies to resources at a level of granularity you choose. The resources in a folder inherit policies and permissions assigned to that folder. A folder can contain projects, other folders, or a combination of both. You can use folders to group projects under an organization in a hierarchy.

## Organization Node
Everything else attached to that account goes under this node, which includes folders, projects, and other resources.
There are some special roles associated with this top-level organization node. For example, you can designate an organization policy administrator so that only people with privilege can change policies. You can also assign a project creator role, which is a great way to control who can create projects and, therefore, who can spend money.

If you have a Workspace domain, Google Cloud projects will automatically belong to your organization node. Otherwise, you can use Cloud Identity, Google’s identity, access, application, and endpoint management platform, to generate one.

Both folders and projects are considered to be “children” of the organization node.

# IAM (Identity and Access Management)
There are three kinds of roles in IAM: basic, predefined, and custom.
Basic roles are quite broad in scope. When applied to a Google Cloud project, they affect all resources in that project. Basic roles include owner, editor, viewer, and billing administrator.
- Project viewers can access resources but can’t make changes.
- Project editors can access and make changes to a resource.
- Project owners can also access and make changes to a resource.
- Billing administrator control the billing for a project but is not able to change the resources in the project.

Specific Google Cloud services offer sets of predefined roles, and they even define where those roles can be applied.

Custom roles will allow you to define those exact permissions.

# Service Accounts
Service accounts allow you to assign specific permissions to a virtual machine, so it can interact with other cloud services without human intervention.
# Cloud Identity
With a tool called Cloud Identity, organizations can define policies and manage their users and groups using the Google Admin Console. Admins can log in and manage Google Cloud resources using the same usernames and passwords they already use in existing Active Directory or LDAP systems. Using Cloud Identity also means that when someone leaves an organization, an administrator can use the Google Admin Console to disable their account and remove them from groups. Cloud Identity is available in a free edition and also in a premium edition that provides capabilities to manage mobile devices.
# Interacting with Google Cloud
The Google Cloud console, the Google Cloud SDK and Cloud Shell, the APIs, and the Google Cloud app.

First is the Google Cloud console, which is Google Cloud’s graphical user interface, or GUI, that helps you deploy, scale, and diagnose production issues in a simple web-based interface.

The Google Cloud SDK is a set of tools that you can use to manage resources and applications hosted on Google Cloud. These include the Google Cloud CLI, which provides the main command-line interface for Google Cloud products and services, and bq, a command-line tool for BigQuery.

Cloud Shell provides command-line access to cloud resources directly from a browser.

The third way to access Google Cloud is through application programming interfaces, or APIs. The Google Cloud console includes a tool called the Google APIs Explorer that shows which APIs are available, and in which versions.

And finally, the fourth way to access and interact with Google Cloud is with the Google Cloud app, which can be used to start, stop, and use SSH to connect to Compute Engine instances and see logs from each instance.