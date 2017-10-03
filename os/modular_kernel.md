# Modular kernel
Using an object-orientated approach each core kernel component is separate and they communicate over some known interface. This means only the necessary code is loaded into memory at boot time.

Moved as much as possible from the kernel into less privileged "user" space (e.g. file system, device drivers). Communication takes place between user modules using message passing

A device driver can run its logic in user space, but when it needs to communicate with the hardware, it must pass a message requesting such to the kernel.

## Benefits
* Easier to develop extensions to the kernel
* Easier to port OS to a new architecture
* More reliable (less code is running in kernel mode). If a device driver fails, it can be re-loaded
* More secure as the kernel is less complex and therefore less likely to have security issues
