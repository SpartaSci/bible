---
tags:
  - hardware
aliases:
  - secure processor
---
**secure processors**: subset of processors with **extra hardware and software security features**. Provide extra logical isolation for software, but they are vulnerable to similar attacks as regular processor

Protected pieces of *code and data* are now called **Enclaves**. Also Trusted Software Modules, whole OS or VM can be Enclaves.

Goal is isolate *secure software* from *un-trusted software*:
- architecture state
- Micro-architectural state ([[hardware/attacks/spectre|spectre]])
- spatial or temporal sharing of HW ([[hardware/attacks/side channel|side channel]])

# baseline problem
The **baseline** of processor HW is un-secure, since considers all the components as trusted. Information can be extracted/modified from the memory, [[cybersec/attacks/snooping|snooping]] on the bus, malicious devices on the I/O interfaces.

The **baseline** of processor SF is un-secure, uses **ring-based protection scheme**, which gives *most privileges* to *lowest levels*, but OS and hypervisor can be compromised.

## new privilege level
Extend with **new privilege levels**:
**Ring 3**: application code
**Ring 2 and 1**: device drivers
**Ring 0**: Operating system kernel
**Ring -1**: HyperVisor or VMM
**Ring -2**: system management mode SMM
**Ring -3**: platform management engine [[hardware/hardware-based security/secure engine|SecE]]


# TEE 
TPC - trusted processor chip 
secure processors lead to [[hardware/hardware-based security/TEE - trusted execution environment|TEE]]
The software executing within a TEE is assumed to be **benign**, so there is no protections from bug and vulnerability in the **protected software**
# protecting state of the protected software
*Protected software's state* is somewhere in the processor, it needs to be protected from un-trusted components. 
**Protect memory** with encryption and integrity [[cybersec/defence/merkle Tree|merkle Tree]]

**Flush or isolate** state
## no-side effect
> secure processor architectures ideally have **No-side effects execution**. Meaning that no side-effect can be **visible** to the un-trusted component whenever protected software is running

The system is in some state -> protected SW run and modify the state -> when it is interrupted **the state modification must be erased**, no bug allowed about this.



# TCB
[[hardware/hardware-based security/TCB - trusted computing base|TCB - trusted computing base]]
> **trusted computing base** is the set of **hardware** and **software** that is responsible for realizing the Trusted Execution Enviroments ([[hardware/hardware-based security/TEE - trusted execution environment|TEEs]])
