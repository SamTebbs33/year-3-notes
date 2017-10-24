# Processes

### OpSys Today

There are a huge number of processes that can be potentially run on a modern operating system, but not all of them are run concurrently. There are clearly far, far more processes in use than processor cores, so the processors time must be effectively managed.

### Concept

The OS executes a variety of programs, including both batch jobs and time-shared systems.

* Process - A program in execution, process execution must progress in sequential fashion.

A process includes the program (text) and a program counter (PC). It also utilises a stack and a data section.

### Process States

To start a new process, a system process calls fork() and allocates resources to the new process, giving it everything it needs to run other than the CPU. There are often more processes ready to run than the CPU is ready to accept. A process may then be accepted to the CPU. From the CPU, a process can be terminated, wait or be returned to the ready state. A waiting process will sit until it receives an interrupt to return to the ready state. If a process has used more than it's fair share of time, it will be returned to the ready state to allow another process to run.

### Process Control Block

Information associated with each process, which is stored as various fields within a kernel data structure includes:

- Process state
- Program counter
- CPU registers
- CPU scheduling information
- Memory-management information (page tables)
- Accounting information (resource usage)
- I/O status information (open files, etc)

This is clearly a large, non-trivial amount of data that must be stored.

### Process Creation

A parent process (the initialisation process) create child processes, which in turn then create other processes, forming a tree. Generally, processes are identified and managed via a process identified (pid).

Resource sharing occurs between processes. Parent processes and their children can share all resources, none of the resources, or perhaps the children share a subset of the parent's resources.

With regards to execution, parent and child processes can either execute concurrently, or parents can wait until child processes terminate.

For instance, if in the terminal one types 'firefox', it will load the browser but the terminal will remain engaged until the firefox process terminates. However, typing 'firefox &' will run the processes concurrently, so that the terminal and firefox can both be running at the same time.

In UNIX, the fork() system call creates new processes, and the exec() system call is used after a fork() to replace the processes memory space with a new program.

### Process Termination

A process executes the last statement and asks the operating system to delete it via exit(). This has two effects; the data is outputted from the child to the parent (via wait()), and the processes resources are deallocated by the operating system.

*Parents can also abort their children.* This can happen if the child has exceeded allocated resources or the task is no longer required. Some Operating Systems don't allow a child to continue without a parent.
