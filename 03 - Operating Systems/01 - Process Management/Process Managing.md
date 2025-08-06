 A system almost always have more tasks to execute then processing units available. 
 Different tasks have different needs, and not always we have the necessary processing power, so, we have to develop strategies to manage the needs of each task.
## Concept of Task
A task is defined as being a execution of a sequencing flux of instructions, built to attend a specific duty.
It's important to highlight the difference between tasks and programs:
- Program: Is a set of one or more sequences of instructions written to resolve a specific problem. The program represent a static concept, without a internal state defined and without interaction with other entities. notepad.exe and vi are an example of programs.
- Task: Is a sequential execution, by a processor, of a sequence of instructions defined in a program to perform it's objective.  It's a dynamic concept, that has a well defined internal state at each instant and interact with others entities: the user, peripherals, other tasks.
Making a simple analogy, we can say that a program is "cake recipe" inside a recipe book (a directory), in a book stand  (disk) in a kitchen (computer). This recipe defines the ingredients (ins) and the preparation (program) of the cake (outs). The "execution" of the recipe, is the task.
## Task managing
A processor has to execute all the tasks submitted by the user. Those tasks have different duration and importance. It's up to the OS to decide in which order to execute.
## Processes
Have 3 basic elements:
- Software Context - Characteristics like: identification, max number of open files, privileges, etc.
- Hardware Context - Registers.
- Addressing Space - The area of memory of the process, where instructions and data are stored for execution.
The OS materializes the process with a Process Control Block - PCB. Inside the PCB are pointer, state, name, priority, registers, memory limits, opened files, etc.
## Process States
**New** - Process being created.
**Executing** - The instructions are being executed.
**Waiting or Blocked** - The process is waiting an event, for instance, I/O.
**Ready** - The process is waiting to be attached to a processor.
**Finished** - The process has finished the execution.
**Zombie** - Can't get the CPU, also known as orphan process.

## Process Managing 
When a process is in executing it's hardware context is stored in the registers. When a process A loses the CPU to a process B, the systems must save the information of process A. The information of process B are loaded, when A gets the CPU again, the state of the registers are restored.
Changing states: 
1. Save process context
2. Update the PCB: Writes new state (ready/blocked/suspended), writes the reason of state change.
3. Moves the PCB to the appropriated queue.
4. Chooses new process to execute.
5. Updates the PCB of the new process and relevant data do the Process Memory.
6. Restores the context of the new process.
### Interruptions x Exceptions
- **Interruptions**: Events caused by external devices to the processor. For example, any I/O device, those events can happen at any time.
	- Process stays in kernel mode
	- Control information is stores in the PCB
	- Manager dispatch another process after treating the interruption.
	- In case of an I/O interruption, the OS can choose the interrupted process to continue executing and save time in the context change. 
- **Exceptions**: Events caused by the processor. Caused during the execution of instructions. For example, dividing by zero.