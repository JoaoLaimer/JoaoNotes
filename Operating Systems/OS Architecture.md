## Monolithic
The operating system is a "solid block" of code that operates in kernel mode, with access to all hardware resources and without memory access restriction.
The advantage of this architecture is the performance: any component can access each other without barriers and without the need to use specific communication protocols between components.
But if a component fails it can lead other to fail as well, because every component is so close to each other. This also lead to higher maintenance cost and time.
Older UNIX systems and the MS-DOS followed this model. Linux kernel is monolithic, but its code is being modularized.
## Monotasks
The first computational systems in the 40s, executed only one task at a time. 
## Microkernels
This idea comes from removing high level code from kernel, leaving only the necessary for accessing the hardware and creating basic abstractions.
The rest of the code is transferred to user space as applications called services. 
This approach offers higher modularity, because each service can be developed independently from each other and can be loaded and deactivated depending of the necessity, leading to higher flexibility;
A microkernel normally implements the notion of tasks, the memory spaces are protected for each application, the communication between each task and interface (i/o) access operations.
All higher level concepts, like processor/memory use policies, file managers, even drivers are implemented outside the kernel.
### Loadable Microkernels
The kernel has a series of components and links additional services using modules. This approach is common in modern UNIX, Solaris, Linux, Mac OS X, and even Windows.
## Layered Systems
Using the notion of layers, we can structure a operating system, where the lower layers interface the hardware, while the intermediary layers give more sophisticated abstractions and management. In the end, the top layers define a kernel interface for applications, called system calls.
The layers have decreasing privilege levels: the lower level has total access to hardware, where the upper layers have a more restricted access.
This approach is inspired by the OSI reference model.
The limitations of this model, is due to, the stacking of various software layers that makes each request travel from a layer to other, decreasing application performance.
Some functionalities are interdependent and doesn't have a way to be layered. For example, managing in/outs needs a memory buffer allocation/freeing service for reading and writing data. What layer comes first?
## Client-Server
The system is divided in processes, being each responsible for offering a series of services: process creation, files, memory.
The server implements specific services.
The clients request services from a server.
The service is requested by the client sending a message to server process, then, the server works and send the response through another message, and the kernel only manages the communication between server and client.
This is a good model for embedded system, because of adaptability.
Normally what is implemented is a combination between layered system and the client-server model. In these cases, the kernel is also responsible for incorporating other critical functions: managing I/O, memory and process scheduling.
