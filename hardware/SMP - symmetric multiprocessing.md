---
tags:
  - memory
---
**Symmetric multiprocessing** or **shared-memory multiprocessing** (**SMP**) involves a [multiprocessor](https://en.wikipedia.org/wiki/Multiprocessor "Multiprocessor") computer hardware and software architecture where two or more identical processors are connected to a single, shared [main memory](https://en.wikipedia.org/wiki/Main_memory "Main memory"), have full access to all input and output devices, and are controlled by a single operating system instance that treats all processors equally, reserving none for special purposes. Most multiprocessor systems today use an SMP architecture. In the case of [multi-core processors](https://en.wikipedia.org/wiki/Multi-core_processor "Multi-core processor"), the SMP architecture applies to the cores, treating them as separate processors.

![imagw](https://upload.wikimedia.org/wikipedia/commons/thumb/1/1c/SMP_-_Symmetric_Multiprocessor_System.svg/1280px-SMP_-_Symmetric_Multiprocessor_System.svg.png)


# protection

[[encryption|Encrypt]] traffic on the bus between processors
- each source-destination pair can share a hard-coded key
- or use distribute keys using public key infrastructure 

Use MACs for the integrity of messages
- again, each source-destination pair can share a key

Use [[merkle Tree]] for memory protection
- can [[snooping|snoop]] on the shared memory bus to update the tree root node as other processors are doing memory accesses
- or pre-processed tree


