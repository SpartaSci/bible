---
tags:
  - memory
---
In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), **distributed shared memory** (**DSM**) is a form of [memory architecture](https://en.wikipedia.org/wiki/Memory_architecture "Memory architecture") where physically separated memories can be addressed as a single shared [address space](https://en.wikipedia.org/wiki/Address_space "Address space"). The term "shared" does not mean that there is a single centralized memory, but that the address space is shared—i.e., the same physical address on two [processors](https://en.wikipedia.org/wiki/Processor_(computing) "Processor (computing)") refers to the same location in memory.

![image](https://www.researchgate.net/publication/2451302/figure/fig2/AS:279882606104581@1443740621557/Structure-of-a-DSM-multiprocessor-using-distributed-directories-Each-processing-node.png)


# protection

[[encryption|Encrypt]] traffic on the bus between processors
- need a shared key

Use MACs for the integrity of messages
- each source-destination pair can share a key

Use [[merkle Tree]] for memory protection
- no longer can snoop on the traffic (DSM is point to point usually)



