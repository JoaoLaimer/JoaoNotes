## Critical Region
Segment of code where threads/processes access the same shared data. We have to guarantee that when a process execute it's critical region, no other process can access it.
To solve this problem some requirements must be satisfied:
- Mutual Exclusion: If process is executing it's critical region no other process can execute on it.
- Progress: No process outside it's critical region can block other process.
- Limited Wait (no starvation): A process can't wait indefinitely to reach it's critical region.

### Solutions
**Disabling Interruptions** - Giving this power to the user may lead to a whole system fault.
**Blocking Variables** - Don't guarantee mutual exclusion, because of race-conditions.
```
while(mutex);
mutex = true;
Critical Region
mutex = false;
```
**Commutative Variables** - Assures mutual exclusion between two processes alternating the execution between critical regions.
	A variable turn indicates which process executes.
```Pa

while (turn != A);
Critical Region A;
turn = B;
```
```Pb
while (turn != B);
Critical Region B;
turn = A;
```

**Non Alternate Communion** - Assures mutual exclusion between two processes without alternating the execution between critical regions.
The "turn" variable indicates each process is up to execute.
"Interested" indicates if a process is ready and wants to execute it's critical region.
A process enters it's critical region if there's no one interested.
If two processes are interested the value of "turn" decides what process gets the critical region.
```Pa
interested[A] = true;
turn = B;
while (interested[B] && turn==B);
Critical Region A;
interested[A] = false;
```
```Pb
interested[B] = true;
turn = A;
while(interested[A] && turn == A);
Critical Region B;
interested[B] = false;
```

- Guarantees mutual exclusion.
- Progress is satisfied.
- Limited wait is satisfied.
## Peterson Algorithm
![[Pasted image 20250603140510.png]]
## TSL Instruction
Atomic Instructions: Modern CPUs have a great number of cores, and a lot of pipeline acceleration techniques.
How can we guarantee atomicity of a set of instructions? Machine instructions introduced in the code by the compiler.
Special hardware instructions (atomic instructions) that allows us to modify a memory work atomically without interruptions.
Those instructions can be used to solve critical sections problems.

**Test and Set Lock Instruction**
Blocking variable "lock".

The "lock" variable is used to guarantee the access to a critical section.
TSL is used to read an update the value of the lock variable atomically.

```P
while TSL(lock);
Critical Region;
lock = false;
```


### Solutions 
All solutions above have **busy wait**.
The blocked process consumes CPU time unnecessarily. 
Spinlocks - Threads still execute in busy wait (consumes cycles), those threads can interrupt the thread that is in it's critical region.

## High Level Synchronization
Must block threads that wait acess (remove the execution, put them in "waiting" state). Allows processes to receive interruption while inside the critical section.
Mechanisms like: 
- Mutex
- Semaphore
- Monitors


