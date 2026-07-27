---
aliases:
  - covert channel
tags:
  - attack
---
[[hardware/_intro/chain/design flow|design flow]]
[[hardware/attack taxonomy/_hardware attack taxonomy|_hardware attack taxonomy]]


designing hardware path

**functional description**: this stage outline what the hardware is supposed to do

**functional specification**: here, we define not only the functionality but also the input ranges, timing requirements, and other relevant parameters

**implementation modeling**: we model the design using tools and [[hardware/VLSI and IP/RTL - register transfer level|RTL]]

**physical implementation**: this involves creating the final system in various form.


# information channel
information flow is an intrinsic part of computing both in a single computer system and a distributed system

Information *processing, communication, storage and sharing*

Many factors: *timing, power and output transition* 


# covert channel
> A covert channel is a path for an illegal flow of information within a system


Any communication channel that a process can exploit to transfer information in a manner that violates the system's security policy


[[hardware/attack taxonomy/side channel/timing attacks|timing]] **covert channel**: accessing the memory or the cache takes different time, this can reveal what kind of data the process accesses

**termination covert channel**

**probability covert channel**

**resource utilization covert channels**

# side channel
> un-intended channel to gain information about the state or operation of the computing system

[[hardware/attack taxonomy/fault attacks/_fault attacks|fault attack]]


[[hardware/attack taxonomy/side channel/power attacks|power]] **side channel**

[[hardware/attack taxonomy/side channel/cache side-channel attacks|cache side-channel attacks]]

[[hardware/attack taxonomy/side channel/cloud-FPGA side-channel attacks|cloud-FPGA side-channel attacks]]


# micro-architectural features

[[hardware/hardware-based security/principles of computer architecture|principles of computer architecture]]

Speculation:
- branch prediction
- speculative execution [[hardware/attack taxonomy/side channel/spectre|spectre]]
- out-of-order execution [[hardware/attack taxonomy/side channel/meltdown|meltdown]]
- Return stack buffer



## characteristics

**existence**

**bandwidth**

**noisy**

