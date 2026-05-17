The primary work case of Compute Engine is any generic workload, especially an enterprise application that was designed to run on a server infrastructure. This makes Compute Engine very portable and easy to run in the cloud. Other services, like Google Kubernetes Engine, which consists of containerized workloads, may not be as easily transferable as what you’re used to from on-premises.

Standard and non-local SSD disks can be sized up to 257 TB for each instance.

## VM Access
For accessing a VM, the creator of an instance has full root privileges on that instance. On a Linux instance, the creator has SSH capability and can use the Google Cloud console to grant SSH capability to other users. On a Windows instance, the creator can use the console to generate a username and password. After that, anyone who knows the username and password can connect to the instance using a Remote Desktop Protocol, or RDP, client.

## Lifecycle
When you define all the properties of an instance and click Create, the instance enters the **provisioning state**. Here the resources such as CPU, memory, and disks are being reserved for the instance, but the instance itself isn’t running yet.
Next, the instance moves to the **staging state** where resources have been acquired and the instance is prepared for launch. Specifically, in this state, Compute Engine is adding IP addresses, booting up the system image, and booting up the system.
After the instance starts running, it will go through pre-configured startup scripts and enable SSH or RDP access.

## Patch Management
The OS patch management service has two main components: Patch compliance reporting, which provides insights on the patch status of your VM instances across Windows and Linux distributions. Along with the insights, you can also view recommendations for your VM instances.

And patch deployment, which automates the operating system and software patch update process. A patch deployment schedules patch jobs. A patch job runs across VM instances and applies patches. There are several tasks that can be performed with patch management.
- You can: Create patch approvals.
- You can select what patches to apply to your system from the full set of updates available for the specific operating system.
- Set up flexible scheduling.
- You can choose when to run patch updates (one-time and recurring schedules).
- Apply advanced patch configuration settings.
- You can customize your patches by adding configurations such as pre and post patching scripts.
- And you can manage these patch jobs or updates from a centralized location.
# Compute Options
There are four Compute Engine machine families: General-purpose, Compute-optimized, Memory-optimized, and Accelerator-optimized.

The general-purpose machine family has the best price-performance with the most flexible vCPU to memory ratios, and provides features that target most standard and cloud-native workloads. 

The E2 machine series is suited for day-to-day computing at a lower cost, especially where there are no application dependencies on a specific CPU architecture.
The Standard E2 VMs have between 2 to 32 vCPUs with a ratio of 0.5 GB to 8 GB of memory per vCPU.
Shared-core E2 machine types have 0.25 to 1 vCPUs with 0.5 GB to 8 GB of memory.

The N2 and N2D are the next generation following the N1 VMs, offering a significant performance jump. N2 VMs support the latest second generation scalable processor from Intel with up to 128 vCPUs and 0.5 to 8 GB of memory per vCPU.

N2D are AMD-based general purpose VMs. They leverage the latest EPYC Milan and EPYC Rome processors, and provide up to 224 vCPUs per node.

Tau T2A and Tau T2D VMs are optimized for cost-effective performance of demanding scale-out workloads. T2D VMs come in predefined VM shapes, with up to 60 vCPUs per VM and 4 GB of memory per vCPU. Tau T2A machine series is the first machine series in Google Cloud to run on Arm processors. The Tau T2A machine series runs on a 64 core Ampere Altra processor with an Arm instruction set and an all-core frequency of 3 GHz.

C2 VMs are the best fit VM type for compute-intensive workloads, including AAA gaming, electronic design automation, and high-performance computing across simulations, genomic analysis, or media transcoding. They might also be applications that have very expensive per core licensing and thus would benefit from higher per core performance. The C2 series comes in different machine types ranging from 4 to 60 vCPUs, and offers up to 240 GB of memory.

C2D VMs are available on the third generation AMD EPYC Milan platform. The C2D machine series come in different machine types ranging from 2 to 112 vCPUs, and offer 4 GB of memory per vCPU .

The H3 series offer 88 cores and 352 GB of DDR5 memory and are available on the Intel Sapphire Rapids CPU platform and Google's custom Intel Infrastructure Processing Unit The memory-optimized machine family provides the most compute and memory resources of any Compute Engine machine family offering.

The M1 machine series has up to 4 TB of memory, while the M2 machine series has up to 12 TB of memory. Both the M1 and M2 machine series offer the lowest cost per GB of memory on Compute M3 VMs offer up to 128 vCPUs, with up to 30.5 GB of memory per vCPU, and are available on the Intel Ice Lake CPU platform.

The A2 series has 12 to 96 vCPUs, and up to 1,360 GB of memory. Each A2 machine type has a fixed number (up to 16) of NVIDIA’s Ampere A100 GPUs attached. Each A2 machine type has a fixed number (up to 16) of NVIDIA’s Ampere A100 GPUs attached.

G2 VMs offer 4 to 96 vCPUs, up to 432 GB of memory, and are available on the Intel Cascade Lake CPU platform.

Custom machine types are ideal for the following scenarios: When you have workloads that are not a good fit for the predefined machine types that are available to you.

# Compute Pricing
The discount is up to 57% for most machine types or custom machine types.
The discount is up to 70% for memory-optimized machine types.
Preemptible and Spot VMs are instances that you can create and run at a much lower price than normal instances. For both types of VM, Compute Engine might terminate (or preempt) these instances if it requires to access those resources for other tasks.
Importantly, preemptible VMs can only run for up to 24 hours at a time, but Spot VMs do not have a maximum runtime.

# Special Compute Options
Shielded VMs offer verifiable integrity to your VM instances, so you can be confident that your instances haven't been compromised by boot or kernel-level malware or rootkits. Shielded VM's verifiable integrity is achieved through the use of Secure Boot, virtual trusted platform module or vTPM-enabled Measured Boot, and integrity monitoring.

Confidential VMs are a breakthrough technology that allows you to encrypt data in use - while it's been processed. A Confidential Virtual Machine is a type of N2D Compute Engine VM instance running on hosts based on the second generation of AMD EPYC processors, code-named "Rome".

# Disks
The first disk that we create is what we call a persistent disk. That means it's going to be attached to the VM through the network interface. This separation of disk and compute allows the disk to survive if the VM terminates.

The choice between HDD and SSD disks comes down to cost and performance. To learn more about disk performance and how it scales with disk size, refer to the link in the course resources for this module. Another cool feature of persistent disks is that you can dynamically resize them, even while they are running and attached to a VM.

Zonal persistent disks offer efficient, reliable block storage.
Regional persistent disks provide active-active disk replication across two zones in the same region. Regional persistent disks deliver durable storage that is synchronously replicated across zones and are a great option for high-performance databases and enterprise applications that also require high availability.

Performance SSD persistent disks are backed by solid-state drives and are suitable for enterprise applications and high-performance databases that require lower latency and more IOPS than standard persistent disks provide.

Balanced persistent disks are also backed by solid-state drives.They are an alternative to SSD persistent disks that balance performance and cost.

Extreme persistent disks are zonal persistent disks also backed by solid-state drives. Extreme persistent disks are designed for high-end database workloads, providing consistently high performance for both random access workloads and bulk throughput.

Local SSDs are different from persistent disks in that they are physically attached to the virtual machine.

You also have the option of using a RAM disk. This will be the fastest type of performance available if you need small data structures.