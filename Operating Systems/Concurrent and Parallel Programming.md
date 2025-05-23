## Parallel
Parallel programming consists in dividing an application in minor pieces to be executed by more than one processing element, but, it has the condition to interact between each other to reach its goal.
A parallel program is composed of processes or thread according to the context in which its inserted.
- In message passing environments (multi-computers) the programs are composed by processes.
- In shared memory environments (multiprocessors) it's composed of threads.
## Concurrent
Concurrent programming is a generalization of parallel programming, because it doesn't really need to have more than one processing element. A concurrent program can execute in an sequential platform (Von Neumman), if it supports multiprogramming.
- Concurrent programming is more complex than sequential.
- A concurrent program can have all kinds of error that appears in a sequential program, and more errors associated to interactions between processes.

## Challenges in Parallel and Concurrent Programming
1. Identifying tasks - Examining applications and finding activities that can be executed simultaneously. 
2. Balancing - Sharing equivalent computational loads to each tasks.
3. Data Sharing - Preventing a threat interfering another.
4. Data Dependency - Controlling and synchronizing threads.
5. Testing and Debugging.
## Kinds of Parallelism
1. Data parallelism - Sharing a quantity of data that will be processed.
2. Tasks parallelism - Sharing different tasks between cores.

## Using PThreads: POSIX API for Threading
A standard defined by IEEE, with portability in mind. The functions defined in the API support basic necessities, like, creating, initializing and ending threads and synchronization function.
Communication in this context is made with shared variables.
