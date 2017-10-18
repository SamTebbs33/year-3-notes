# Kernel programming

Simplified kernel structure:

```
while(true) {
  while(timer not gone off) {
    assign CPU to suitable process
    execute process
  }
  select next suitable process
}
```

The kernel has access to all resources and not is subject to any constraints for memory and hardware access.

The kernel provides its functions as system calls, which are abstracted by the C stdlib. There is strict separation of kernel data and user program data.

## Interrupts
When the kernel asks the hardware to perform some action, it triggers an interrupt when done, which is caught by the kernel. Kernel distributes the interrupt or handles it itself (must be done quickly).

Interrupts have a priority level and those of higher priorities are prioritised (what a surprise) over those of lower priority.

## Kernel modes
The structure of the kernel gives rise to two modes of operation:

* **Process context**: the kernel is working for a user program by executing a system call
* **Interrupt context**: the kernel is handling and interrupt

The kernel only has access to user data in the process context. Any code running in the process context may be pre-empted at any time by an interrupt.

## Kernel modules
Using an object-orientated approach each core kernel component is separate and they communicate over some known interface. This means only the necessary code is loaded into memory at boot-time and new modules can be added at run-time. Useful if certain drivers are only required if the relevant hardware is present.

Moved as much as possible from the kernel into less privileged "user" space (e.g. file system, device drivers). Communication takes place between user modules using message passing

A device driver can run its logic in user space, but when it needs to communicate with the hardware, it must pass a message requesting such to the kernel.

## Benefits
* Easier to develop extensions to the kernel
* Easier to port OS to a new architecture
* More reliable (less code is running in kernel mode). If a device driver fails, it can be re-loaded
* More secure as the kernel is less complex and therefore less likely to have security issues

## Concurrency in kernel
Correct handling of concurrency in the kernel is important as it manipulates data structures shared between code running in process mode and interrupt mode.

Concurrency usage must only happen when absolutely necessary to mitigate the associated issues.

## Achieving mutual exclusion
* **Semaphores/mutex**: When entering a __critical section__ fails, the current process is put to sleep until the section is available. Only usable if all critical sections are in the process context
* **Spinlocks**: The processor repeatedly tries to enter the critical section of code. Usable anywhere

## Data transfer between user space and kernel
Linux maintains a directory called **proc** as an interface between user space and the kernel. Files in this directory don't actually exist on disk. Read and write operations on these files are translated into kernel operations, together with data transfer between user space and the kernel.

## Parts of the Linux kernel
* Drivers in the **drivers** directory, sorted according to category
* File systems in the **fs** directory
* Scheduling and process management in the **kernel** directory
* Networking code in the **net** directory
* Low-level architecture specific code in the **arch** directory
* Include-files in the **include** directory
