# Memory management

## Memory mapping
A program and the hardware both see memory as a set of memory cells starting at address 0x0. A program's addresses (logical addressing) don't always correspond to the same address in hardware (physical addressing). Logical addresses are mapped to physical addresses

The mapping can be made at:
* **Compile-time**: Absolute references are generated, restrictive
* **Load-time**: ??
* **Execution-time**: Needs hardware support

Dynamic linking makes one copy of a system library available to multiple processes to avoid it being unnecessarily re-copied.

## Virtual memory (swapping)
If memory demand is too high, the memory of some processes is transferred to disk. When combined with scheduling, the memory of low priority processes is swapped out.

## Fragmentation
Swapping raises two problems:
* **External fragmentation**: Many small holes appear in memory. If 1GB of space is spread across two (non consecutive) holes and a new process requires 1GB, the occupied space in between needs to be moved.
* **Internal fragmentation**: wtf is this

Strategies for choosing holes of memory:
* **First-fit**: Start from beginning and use first available hole
* **Rotating first-fit**: Like first-fit but start from last assigned part of memory
* **Best-fit**: Find the smallest usable space
* **Buddy system**: Memory is split into a binary tree. The capacity of a node in the tree is the sum of its children.
