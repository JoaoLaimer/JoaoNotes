The OS must act in many fronts.
### Processor Manager
A.k.a Process, task, activities manager, divides the processing capabilities in a fair way between applications.
The OS provides an illusion that exists an processing unit to each task, which facilitates the work on applications by programmers.
It's also the duty of the processor manager to synchronize tasks.
## Memory Manager
Has the objective of giving each application an area of memory, independent and isolated from the other including the operating system.
The isolating of memory areas, increases stability and system security, because it impedes applications from interfering the functioning of others.
If the RAM is insufficient the OS can increase it using the disk.
An important abstraction is "virtual memory".
## Devices Manager
Each peripheral  has it's own particularities. The Os has to implement an interaction between  each devices by using an driver, and using abstract models that allows grouping similar devices.
## Files Manager
This is responsible by creating files and directories, defining its accesses and rules of use.
## Security Manager
It's important to define clear rules to each resource that an user can access (read, write, execute) and guarantee that the rules are being followed.