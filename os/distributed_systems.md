# Distributed systems

Aims:
* **Resource sharing**: Costly resources (printers, expensive programs) can be shared
* **Computation speedup**: Concurrently running algorithms across multiple machines can speed up computation
* **Reliability**: Failure of one thing doesn't imply failure of the whole system

Levels of distribution (listed from tightly coupled to loosely coupled):
* Shared memory
* Shared filesystem
* Bus systems
* Switching systems

## Communication
Communication across distributed systems can be achieved through

* **Client/Server**: Group of processes (servers) used by clients
  * Simple communication
  * Addressing the server
    * **Hardware address in code**: Inflexible
    * **Broadcasting**: Only works on local networks, clogs up network
    * **Name servers**: Ask special known host, e.g. DNS
  * Blocking vs non-blocking? Conceptual and design ease vs performance
* **Remote procedure call**: Execute procedure on another host
  1. Client sends arguments to server
  2. Server executes
  3. Server sends result back
  * What do you do with call-by-reference parameters? Arrays can be copied but it's more difficult with arbitrary data structures
