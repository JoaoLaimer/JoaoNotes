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

# Virtual Private Cloud Networking
A virtual private cloud, or VPC, is a secure, individual, private cloud-computing model hosted within a public cloud.
VPC networks connect Google Cloud resources to each other and to the internet. This includes segmenting networks, using firewall rules to restrict access to instances, and creating static routes to forward traffic to specific destinations.
Google VPC networks are global. They can also have subnets, which is a segmented piece of the larger network, in any Google Cloud region worldwide. Subnets can span the zones that make up a region.
# Compute Engine
With Compute Engine, users can create and run virtual machines on Google infrastructure.

For the use of virtual machines, Compute Engine bills by the second with a one-minute minimum, and sustained-use discounts start to apply automatically to virtual machines the longer they run. So, for each VM that runs for more than 25% of a month, Compute Engine automatically applies a discount for every additional minute.

Compute Engine also offers committed-use discounts. This means that for stable and predictable workloads, a specific amount of vCPUs and memory can be purchased for up to a 57% discount off of normal prices in return for committing to a usage term of one year or three years.

And then there are Preemptible and Spot VMs.
You can save money, in some cases up to 90%, by choosing Preemptible or Spot VMs to run the job. A Preemptible or Spot VM is different from an ordinary Compute Engine VM in only one respect: Compute Engine has permission to terminate a job if its resources are needed elsewhere. Although savings are possible with preemptible or spot VMs, you'll need to ensure that your job can be stopped and restarted.

Spot VMs differ from Preemptible VMs by offering more features. For example, preemptible VMs can only run for up to 24 hours at a time, but Spot VMs do not have a maximum runtime. However, the pricing is, currently the same for both.

In terms of storage, Compute Engine doesn’t require a particular option or machine type to get high throughput between processing and persistent disks. That’s the default, and it comes to you at no extra cost.

# Scaling Virtual Machines
Compute Engine has a feature called Autoscaling, where VMs can be added to or subtracted from an application based on load metrics. The other part of making that work is balancing the incoming traffic among the VMs.

# Important VPC Compatibilities
VPC routing tables are built-in so you don’t have to provision or manage a router. They’re used to forward traffic from one instance to another within the same network, across subnetworks, or even between Google Cloud zones, without requiring an external IP address.

VPCs provide a global distributed firewall, which can be controlled to restrict access to instances through both incoming and outgoing traffic. Firewall rules can be defined through network tags on Compute Engine instances, which is really convenient. For example, you can tag all your web servers with, say, “WEB,” and write a firewall rule saying that traffic on ports 80 or 443 is allowed into all VMs with the “WEB” tag, no matter what their IP address happens to be.

With VPC Peering, a relationship between two VPCs can be established to exchange traffic. Alternatively, to use the full power of Identity Access Management (IAM) to control who and what in one project can interact with a VPC in another, you can configure a shared VPC.

# Cloud Load Balancing
The job of a load balancer is to distribute user traffic across multiple instances of an application. Cloud Load Balancing is a fully distributed, software-defined, managed service for all your traffic.

Cloud Load Balancing provides cross-region load balancing, including automatic multi-region failover, which gently moves traffic in fractions if backends become unhealthy. Cloud Load Balancing reacts quickly to changes in users, traffic, network, backend health, and other related conditions.

Application Load Balancers operate at the application layer and are designed to handle HTTP and HTTPS traffic, making them ideal for web applications and services that require advanced features like content-based routing and SSL/TLS termination. Application Load Balancers operate as reverse proxies, distributing incoming traffic across multiple backend instances based on rules you define.

Network Load Balancers operate at the transport layer and efficiently handle TCP, UDP, and other IP protocols. They can be further classified into two types: Proxy Network Load Balancers also function as reverse proxies, terminating client connections and establishing new ones to backend services.

Unlike proxy Network Load Balancers, passthrough Network Load Balancers do not modify or terminate connections.

# Cloud DNS and Cloud CDN
Google Cloud offers Cloud DNS to help the world find them. It’s a managed DNS service that runs on the same infrastructure as Google. It has low latency and high availability, and it’s a cost-effective way to make your applications and services available to your users. The DNS information you publish is served from redundant locations around the world.

You can use this system to accelerate content delivery in your application by using Cloud CDN - Content Delivery Network.

# Connecting Networks to Google VPC
To start with a Virtual Private Network connection over the internet and use Cloud VPN to create a “tunnel” connection. To make the connection dynamic, a Google Cloud feature called Cloud Router can be used.

Cloud Router lets other networks and Google VPC, exchange route information over the VPN using the Border Gateway Protocol. Using this method, if you add a new subnet to your Google VPC, your on-premises network will automatically get routes to it.

So, a second option is to consider “peering” with Google using Direct Peering. Peering means putting a router in the same public data center as a Google point of presence and using it to exchange traffic between networks. Customers who aren’t already in a point of presence can work with a partner in the Carrier Peering program to get connected. One downside of peering though, is that it isn’t covered by a Google Service Level Agreement.

A Partner Interconnect connection is useful if a data center is in a physical location that can't reach a Dedicated Interconnect colocation facility, or if the data needs don’t warrant an entire 10 Gigabytes per second connection.

Cross-Cloud Interconnect helps you establish high-bandwidth dedicated connectivity between Google Cloud and another cloud service provider. Google provisions a dedicated physical connection between the Google network and that of another cloud service provider.  

# Cloud Storage
Cloud Storage is Google’s object storage product. Cloud Storage’s primary use is whenever binary large-object storage (also known as a “BLOB”) is needed for online content such as videos and photos, for backup and archived data and for storage of intermediate results in processing workflows.

A bucket needs a globally unique name and a specific geographic location for where it should be stored, and an ideal location for a bucket is where latency is minimized. The storage objects offered by Cloud Storage are immutable, which means that you do not edit them, but instead a new version is created with every change made.
If you choose to use versioning, Cloud Storage will keep a detailed history of modifications -- that is, overwrites or deletes -- of all objects contained in that bucket.
## Storage Classes and Data Transfer
There are four primary storage classes in Cloud Storage.

Standard Storage is considered best for frequently accessed, or “hot,” data. It’s also great for data that’s stored for only brief periods of time.

Nearline Storage, is best for storing infrequently accessed data, like reading or modifying data on average once a month or less. Examples might include data backups, long-tail multimedia content, or data archiving.

Coldline Storage. This is also a low-cost option for storing infrequently accessed data. However, as compared to Nearline Storage, Coldline Storage is meant for reading or modifying data, at most, once every 90 days.

Archive Storage. This is the lowest-cost option, used ideally for data archiving, online backup, and disaster recovery. It’s the best choice for data that you plan to access less than once a year, because it has higher costs for data access and operations and a 365-day minimum storage duration.

Although each of these four classes has differences, it’s worth noting there are several characteristics that apply across all of these storage classes. These include: Unlimited storage with no minimum object size requirement, worldwide accessibility and locations, low latency and high durability, a uniform experience, which extends to security, tools, and APIs, and geo-redundancy if data is stored in a multi-region or dual-region.

Cloud Storage also provides a feature called Autoclass, which automatically transitions objects to appropriate storage classes based on each object's access pattern.

Storage Transfer Service enables you to import large amounts of online data into Cloud Storage quickly and cost-effectively. The Storage Transfer Service lets you schedule and manage batch transfers to Cloud Storage from another cloud provider, from a different Cloud Storage region, or from an HTTP(S) endpoint.
And then there is the Transfer Appliance, which is a rackable, high-capacity storage server that you lease from Google Cloud. You connect it to your network, load it with data, and then ship it to an upload facility where the data is uploaded to Cloud Storage.

## Cloud SQL
Cloud SQL offers fully managed relational databases, including MySQL, PostgreSQL, and SQL Server as a service. Cloud SQL doesn't require any software installation or maintenance. It can scale up to 128 processor cores, 864 GB of RAM, and 64 TB of storage.
## Spanner
Spanner is a fully managed relational database service that scales horizontally, is strongly consistent, and speaks SQL. Battle tested by Google’s own mission-critical applications and services, Spanner is the service that powers Google’s $80 billion business. Spanner is especially suited for applications that require a SQL relational database management system with joins and secondary indexes, built-in high availability, strong global consistency, and high numbers of input and output operations per second.
## Firestore
Firestore is a flexible, horizontally scalable, NoSQL cloud database for mobile, web, and server development. With Firestore, data is stored in documents and then organized into collections.
## Bigtable
Bigtable is designed to handle massive workloads at consistent low latency and high throughput, so it's a great choice for both operational and analytical applications, including Internet of Things, user analytics, and financial data analysis.
## Comparing Storage Options

| Option        | Best For                                                                                                                                                  | Capacity                                               |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------ |
| Cloud Storage | Storing immutable blobs larger than 10 MB                                                                                                                 | Petabytes. Max unit size: 5 TB per object.             |
| Cloud SQL     | Full SQL support for an online transaction processing system.<br>Web Frameworks and existing applications                                                 | Up to 64 TB<br>                                        |
| Spanner       | Full SQL support for an online transactional processing system<br>Horizontal scalability                                                                  | Petabytes                                              |
| Firestore     | Masive scaling and predictability together with real time query results and offline query support                                                         | Terabytes<br>Max unit size: 1 MB per entity            |
| Bigtable      | Storing large amount of structured objects<br>Does not support SQL queries and multi-row transactions<br>Analytical data with heavy read and write events | Petabytes<br>Max unit size: 10 MB p/cell, 100 MB p/row |
# Kubernetes
Kubernetes is an open-source platform for managing containerized workloads and services. It makes it easy to orchestrate many containers on many hosts, scale them as microservices, and easily deploy rollouts and rollbacks. At the highest level, Kubernetes is a set of APIs that you can use to deploy containers on a set of nodes called a cluster. The system is divided into a set of primary components that run as the control plane and a set of nodes that run containers.

In Kubernetes, a node represents a computing instance, like a machine.
A Pod is the smallest unit in Kubernetes that you can create or deploy.

Instead of issuing commands, you provide a configuration file that tells Kubernetes what you want your desired state to look like, and Kubernetes determines how to do it. You accomplish this by using a Deployment config file.

# Google Kubernetes Engine
GKE is a Google-hosted managed Kubernetes service in the cloud. The GKE environment consists of multiple machines, specifically Compute Engine instances, grouped together to form a cluster.

GKE manages all the control plane components for us. It still exposes an IP address to which we send all of our Kubernetes API GKE manages all the control plane components for us. It still exposes an IP address to which we send all of our Kubernetes API.

With the Autopilot mode, which is recommended, GKE manages the underlying infrastructure such as node configuration, autoscaling, auto-upgrades, baseline security configurations, and baseline networking configuration. With the Standard mode, you manage the underlying infrastructure, including configuring the individual nodes.

# Cloud Run
Is a managed compute platform that runs stateless containers via web requests or Pub/Sub events. Cloud Run is serverless. That means it removes all infrastructure management tasks so you can focus on developing applications. It’s built on Knative, an open API and runtime environment built on Kubernetes.
You can use a container-based workflow, as well as a source-based workflow. The source-based approach will deploy source code instead of a container image.

# Cloud Run Functions
With Cloud Run functions, you write a single-purpose function that completes the necessary image manipulations and then arrange for it to automatically run whenever a new image is uploaded.