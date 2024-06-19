---
tags:
  - hardware
aliases:
  - TCB
---
important links to [[hardware/TEE - trusted execution environment|TEE]] and [[hardware/TPM - Trusted Platform Module|TPM]]


> **trusted computing base** is the set of **hardware** and **software** that is responsible for realizing the Trusted Execution Enviroments ([[hardware/TEE - trusted execution environment|TEEs]])


[[hardware/TEE - trusted execution environment|TEE]] is created by a set of all the components in the TCB

TCB is trusted to implement the protections correctly, otherwise Vulnerabilities in the TCB can **compromise** the security of the entire system
ideally:
- rooted in hardware and small
- should be isolated from the rest of the computing components
- its correctness and runtime state should be easily and independently verifiable 


at he heart of the TCB is the [[hardware/TPM - Trusted Platform Module|TPM - Trusted Platform Module]]


