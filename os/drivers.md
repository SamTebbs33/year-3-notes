# Device drivers

From user space, each driver is seen as a file to which a user program can read and write. From kernel space, each driver file has functions associated with them which are called when certain system calls are made. Each driver implements at least `read`, `write`, `open` and `close`.

The kernel also keeps track of:
* **Physical dependencies**: What devices are connected to USB hubs etc.
* **Buses**: Channels between processor and one or more devices can be either physical or logical
* **ClasseS**: Sets of devices of same type (keyboards, mice etc.)

## Interrupt handling
1. Device sends interrupt
2. CPU selects appropriate interrupt handler
3. Handler processes the interrupt
  * Data is transferred to/from the device
  * Wake up processes which wait for data transfer to be finished
4. Handler clears interrupt bit of the device, which is necessary for the next interrupt to arrive

Interrupt processing time must be as short as possible
  * **Top half**: Called directly by interrupt handler. Only transfer data between device and appropriate kernel buffer and schedules software interrupt to start __bottom half__ (this is higher level and more abstracted than bottom half)
  * **Bottom half**: Runs in the interrupt context and does the lower level processing (working through protocol stack, and waking up processes)
