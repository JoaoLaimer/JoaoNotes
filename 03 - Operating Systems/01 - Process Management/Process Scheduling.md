A scheduling policy must be built to achieve:
- Maintaining the processor busy at all times.
- Maximizing throughput.
- Offering reasonable response times
- Privileging critical applications execution.
- Minimizing turnaround time (Time interval since a process is admitted and finished).
- Resource use balancing.

#### Long Term Scheduler
Chooses which program will be staged in the system for processing. Selects processes from the secondary memory to the main memory, controls the multiprogramming level. Example: A new process is initialized, the OS decides which resources are sufficient to execute it.
#### Medium Term Scheduler
Managing swapping of processes, when the need of freeing the main memory to other processes comes. Example: When the RAM is full, the OS moves a inactive process to disk.
#### Short Term Scheduler
Executes frequently and decides which process will be next. Example: Each fraction of second, the OS chooses which process in RAM uses the CPU.
- Clock interruptions.
- I/O interruptions.
- When a process is created or ended.
- Signals (Semaphores).

## Non-Preemptive (or Cooperative Scheduling)
When a process gets hold of the CPU, it executes til it's blocked (I/O) or when it frees the CPU voluntarily. A process can't be interrupted to give in the CPU to another process. Saves resources not changing context. 
## Preemptive
A process in execution can be interrupted by the OS and the CPU is given to another process. Allows the system to prioritize processes.
# Batch Processing
Doesn't have explicit temporal requisites, can be non-preemptive or preemptive. It's used to maximize throughput, turnaround and CPU utilization.
# Interactive Processing
A preemptive processing type where minimizing the response time is essential and should satisfy the user expectations guaranteeing proportionality. 
# Real Time Processing
Generally uses preemptive policies, focusing in achieving deadlines. It's predictable, each process must use the same time.

Every scheduler must achieve:
- Justice - give a each process a fair share of the CPU, avoiding starvation.
- Guarantee the scheduling policy.
- Balance - maintaining each part of the system equally busy.
## Scheduling Criterion
- Turnaround Time (Tr) or Time of life (Tl)  - Time between the creation of a task and it's end.
- Time of Wait (Tw) - Time lost by the task in the ready queue.
- Time of Response (Tr) - Time between the arrival of an event to the system and the response for it.
- Time of Service (Execution) (Tx) - CPU time.
- Justice - Fair distribution of processor shares between ready tasks. 