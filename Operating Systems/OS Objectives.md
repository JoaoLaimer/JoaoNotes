The primary objective of an Operating Systems can be synthesized in two key-words: "abstraction" and "managing".
## What is a Operating System?
Is a program that manages the hardware of a computer.
## Resources Abstraction 
Accessing hardware resources of a computer can be a complex task, because of the specific characteristics of each physical devices and it's interfaces.
Here's the main steps involved in the opening of a simple file on disk:
1. verify if the parameters informed are correct (file name, disk identifier, read buffer, etc).
2. verify if the disk is ready;
3. turn on the disk motor and wait it to reach the correct rotational speed;
4. position the read head above the trail the directory table is located.
5. read the table and find the file in the sub-directory;
6. move the read head to the initial block of the file;
7. read the initial block of the file and put it on the memory buffer;
With this, the OS must define abstract interfaces to the hardware:
- Provide interfaces to access device, simpler to use than the low level interfaces.
- Turn apps independent to hardware
- Define homogeneous access interfaces to devices of distinct technologies.
## Resource Managing
Normally every computer has less processors than the number of task in execution.  With this, the use of these processors must be distributed between applications on the system, in a way that each one of them can execute in an acceptable speed without harming others. The same occurs in RAM, where it must be distributed between apps.



