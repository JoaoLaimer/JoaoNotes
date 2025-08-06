# First Come First Served
Simple scheduling policies, as soon as a process is ready it enters a ready queue. When a process frees the CPU, the system selects the first process of the queue to execute.
Non-Preemptive.
CPU-bound processes in front of the queue can harm I/O-bound processes.
Short processes have to wait too much time in queue, when it arrives after a long process.

| Process | Arrival Time | Execution Time (Tx) | Start Time | End Time | Turnaround Time | Tr/Tx |
| ------- | ------------ | ------------------- | ---------- | -------- | --------------- | ----- |
| W       | 0            | 1                   | 0          | 1        | 1               | 1,0   |
| X       | 1            | 100                 | 100        | 101      | 100             | 1,0   |
| Y       | 2            | 1                   | 101        | 102      | 100             | 100,0 |
| Z       | 3            | 100                 | 102        | 202      | 199             | 1,99  |
# Shortest Job First or Shortest Job Next
SJF or SJN, or even Shortest Process Next, is a non-preemptive algorithm. It selects, from a ready list, processes with shortest execution time waiting. It was proposed in a tentative to better the performance of shorter processes. A difficulty is to estimate the execution time of processes.
Turnaround time is shorter for shorter processes than FCFS
Causes starvation in longer processes.

| Process | Arrival Time | Service Time |
| ------- | ------------ | ------------ |
| A       | 0            | 3            |
| B       | 2            | 6            |
| C       | 4            | 4            |
| D       | 6            | 5            |
| E       | 8            | 2            |
![[SJFos IMG.png]]
# Shortest Remaining Time
Preemptive version of Shortest Job First, the scheduler chooses the process with the shortest time remaining, the scheduler interrupts the process in execution when a process with a shorter time remaining becomes ready.
Has a difficulty to estimate the execution time of processes and longer processes can starve.

| Process | Arrival Time | Service Time |
| ------- | ------------ | ------------ |
| A       | 0            | 3            |
| B       | 2            | 6            |
| C       | 4            | 4            |
| D       | 6            | 5            |
| E       | 8            | 2            |
![[OSsrt IMG.png]]
# Round Robin
Circular scheduling, is a preemptive policy. Is established a slice of time called quantum which a process can execute on. At the end of it's time, the process is interrupted, put in a ready queue and the next process in line is selected.
A interruption in the clock is generated at each quantum. I/O bound processes are usually harmed if they don't use their quantum.
It's a policy created for shared time systems.
If the quantum is too small it favor shorter processes, but wastes too much time in context changes, if the quantum is too large, it results in larger response times.
Typical values:

| System                          | Quantum (Time slice)                          |
| ------------------------------- | --------------------------------------------- |
| Desktop (Linux/Windows/macOS)   | 10 ms - 100 ms                                |
| Servers                         | 20 ms - 200 ms (priority in throughput)       |
| Real time operating systems     | 1 ms - 10 ms (predictability)                 |
| Modern Kernels (ex.: Linux CFS) | Dynamic (adjustable, typically 6 ms - 100 ms) |
#### quantum = 1

| Process | Arrival Time | Service Time |
| ------- | ------------ | ------------ |
| A       | 0            | 3            |
| B       | 2            | 6            |
| C       | 4            | 4            |
| D       | 6            | 5            |
| E       | 8            | 2            |
![[RRq1os IMG.png]]
#### quantum = 4
![[RRq4os IMG.png]]
### Virtual Round Robin
Is a refinement of round robin, it's makes so I/O-bound processes are not harmed in relation of CPU-bound processes. There are two queues, ready queue and auxiliary ready queue, if a process loses the CPU to execute I/O, when it's ready again hes put in the auxiliary queue. The auxiliary queue has a greater priority.

# Priorities
The priority queue can be preemptive and non-preemptive, processes with lower priority can suffer from starvation, a solution to it is using aging, processes with higher age are prioritized.

### PRIOc Scheduling
Cooperative priority, non-preemptive, a higher priority process doesn't interrupt another process.
### PRIOp Scheduling
Preemptive priority, a higher priority process interrupt another process.
## Dynamic Priorities
Static priorities can cause starvation to lower priority processes, to solve this we can use dynamic priorities to raise the priority of waiting processes, when executed the processes reverts to it's original priority, using the aging algorithm.
### PRIOd Scheduling
Preemptive dynamic priority. The processes priority raises with time, when the processes it's executed the priority reverts. 
## Defining Priorities
External Factors:
- Information provided by user or admin.
- The scheduler can't estimated alone.
- Defines a static priority.
Internal Factors:
- Information that the scheduler can obtain.
- Can be used to estimate with internal data - Task Age, Estimated Duration, Interactivity, Waiting Time.
- Can calculate a dynamic priority.