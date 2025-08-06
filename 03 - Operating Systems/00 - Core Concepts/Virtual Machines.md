A virtual machine is a software that "transforms" a system into another, that uses the services from a operating system to build the interface for another system.
A virtual machine environment consists in three basic parts:
- The real operating system (HOST), that have the real hardware and software resources.
- A virtualization layer, called hypervisor or VMM (Virtual Machine Monitor), that builds the virtual machine using the host's resources.
- The virtual machine system, called guest; sometimes, more than one can coexist, executing on top of the same system.
There are multiple kinds of hypervisors:
- Application Hypervisor: supports the execution of a application in a specific language. For example: JVM (Java Virtual Machine), CLR (Common Language Runtime, for C#).
- System Hypervisor: supports the execution of a guest operating system.
	- Type 1 (Bare Metal, Native): execute directly on hardware, "virtualizing" the resources of it to build virtual machines.
	- Type 2 (Hosted): execute on top of an host operating system. VMWare, VirtualBox.

Some advantages of using virtual machines:
- Code portability (JVM)
- Server consolidation: Using sub-utilized resources to virtualize a system, reducing infrastructure costs.
- Availability: restoring a copy of a VM to other server.
- Easy scalability and load balancing.
- Software Development: isolated environments for testing sofware.