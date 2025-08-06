## Dining Philosophers Problem
Five philosophers dine together in the same table. Each philosopher has their own plate at the table. There is a fork between each plate. The dish can only be eaten with two forks. Each philosopher can either think or eat. A philosopher can only eat when they have both the left and right fork. Thus the forks will be available when their two nearest neighbors are thinking. 
The problem occurs when a philosopher holds only one fork (resource holding).

## Deadlocks
Happens when tasks groups are blocked while waiting for each other. 
Example: Task 1 is waiting for Task 2 to start, Task 2 is waiting for Task 3 to start, Task 3 is waiting for Task 1 to start.
There are four conditions for a deadlock to happen:
- Mutual Exclusion: multiple resources are not shareable; only one process at a time may use each resource.
- Hold and Wait or resource holding: a process is currently holding at least one resource and requesting additional resources which are being held by another process.
- No preemption: a resource can be released only voluntarily by the process holding it.
- Circular wait: each process must be waiting for a resource which is being held by another process, which in turn is waiting for the first process to release the resource.
While these conditions are sufficient to produce a deadlock on single-instance resource systems, they only indicate the possibility of deadlock on systems having multiple instances of resources.

## Resource Allocation Graph
Way to represent resource allocation between tasks, it allows for visualizing any issues.
A set of vertices V, split into Processes and Resouces.
- P = {P1, P2, P3, ..., Pn}
- R = {R1, R2, R3, ..., Rn}
An edge starting from P to R, means a process is waiting for a resource (Request Edge)
An edge starting from R to P, means the resource is allocated to the process (Assign Edge)

A process is represented by a Circle ( O ): P1
A resource is represented by a Square ( [  ] ): R1
A assignment is represented like ( [  ] -> O ): P1 has R1
A request is represented like ( O - -> [  ] ) : P1 wants R1
Two resources of the same kind is represented by a rectangle with two full circles inside it.

## Strategies to mitigate deadlocks
- Ignore: the deadlock is a problem for the programmer.
- Prevent: programming rules to avoid deadlocks.
- Avoid: monitoring the use of resources and avoid deadlocks
- Detect: detect the occurrences of deadlocks and undo them. 
The most used in OSs is: Ignore

The ostrich algorithm (Tanenbaum): Just bury your head in the sand and pretend nothing is happening.
The majority of OSs, just ignore the problem:
- Is better to have an occasional deadlock then to restrict the user to a process at a time.
- Mitigating deadlocks have a high computational cost (implementing non conventional restrictions).
- It's better to take this load of the OS and give it to the system programmer.
## Manipulating Deadlocks
A deadlock to occur, it needs mutual exclusion, circular wait, no-preemption, and resource holding.

Ensuring that at least one of the conditions does not occur will avoid deadlock.
- 1) Mutual Exclusion: Guarantee that resources will always be shared simultaneously, reduce the exclusion areas to a minimum, and alternative strategies like spooling (printers).
- 2) Hold and wait: All request must comes from the beginning, or when a process requests a resource it has to free all resources it already has. Can cause starvation.
- 3) No-Preemption: Yank resources from tasks, and sabe it's state so you can restore later. Can cause inconsistency.
- 4) Circular wait: Sorting algorithms.

**Safe State**: When a system can allocated resources in a specific order and continue avoiding deadlock.

#### Avoiding Deadlock
- Follow resource allocation to tasks and deny any resource access that can reach a unsafe state.