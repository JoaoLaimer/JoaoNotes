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
## Shortest Remaining Time
