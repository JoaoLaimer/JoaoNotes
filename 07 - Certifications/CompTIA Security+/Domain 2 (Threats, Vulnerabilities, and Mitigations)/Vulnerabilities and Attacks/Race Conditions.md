Software vulnerability where the outcome depends on the timing of events not matching the developer's intended order.
Race conditions occur when multiple threads write to the same variable or object in the same memory location simultaneously.
## Dereferencing
A fundamental operation in programming, and the vulnerabilities arise from unsafe or concurrent usage, particularly in scenarios involving race conditions.
### Dirty COW
Popular 2016 exploit, showcasing a race condition exploitation.
**Copy-on-Write**

## Time-of-Check (TOC)
Type of race condition where an attacker can alter a system resource after an application checks its state but before the operation is performed.
## Time-of-Use (TOU)
Type of race condition that occurs when an attacker can change the state of a system resource between the time it is checked and the time it is used.

> TOC and TOU are two critical moments within the same vulnerability, which is categorized as a race condition.

## Time-of-Evaluation (TOE)
Type of race condition that involves the manipulation of data or resources during the time window when a system is making a decision or evaluation.

## Time of Check to Time of Use (TOCTOU)
Also called a state attack.
## Mutex
Mutually exclusive flag that acts as a gatekeeper toa section of code so that only one thread can be processed at a time.
## Deadlock
Occurs when two or more processe are unable to proceed because each is waiting for the other to release a resource.
