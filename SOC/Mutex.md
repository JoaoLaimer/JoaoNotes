## Critical Region
Segment of code where threads/processes access the same shared data. We have to guarantee that when a process execute it's critical region, no other process can access it.
To solve this problem some requirements must be satisfied:
- Mutual Exclusion: If process is executing it's critical region no other process can execute on it.
- Progress: No process outside it's critical region can block other process.
- Limited Wait (no starvation): A process can't wait indefinitely to reach it's critical region.

### Solutions
**Disabling Interruptions** - Giving this power to the user may lead to a whole system fault.
**Blocking Variables** - Don't guarantee mutual exclusion, because of race-conditions.
**Commutative Variables** - Assures mutual exclusion between two processes alternating the execution between critical regions.
	A variable turn indicates which process executes.