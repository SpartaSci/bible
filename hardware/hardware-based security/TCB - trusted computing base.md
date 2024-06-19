---
tags:
  - hardware
aliases:
  - TCB
---
important links to [[hardware/hardware-based security/TEE - trusted execution environment|TEE]] and [[hardware/hardware trust/TPM - Trusted Platform Module|TPM]]


> **trusted computing base** is the set of **hardware** and **software** that is responsible for realizing the Trusted Execution Environments ([[hardware/hardware-based security/TEE - trusted execution environment|TEEs]])


[[hardware/hardware-based security/TEE - trusted execution environment|TEE]] is created by a set of all the components in the TCB and at he heart of the TCB there is the [[hardware/hardware trust/TPM - Trusted Platform Module|TPM - Trusted Platform Module]]



TCB is trusted to implement the protections correctly, otherwise Vulnerabilities in the TCB can **compromise** the security of the entire system and [[hardware/hardware-based security/TEE - trusted execution environment|TEE]] ^37e331

ideally: 
- rooted in hardware and small
- should be isolated from the rest of the computing components
- its correctness and runtime state should be easily and independently verifiable 

TCB can be implemented as *dedicated circuits*, custom logic or hardware state machine, or as firmware running on *dedicated processor* [[hardware/hardware-based security/secure engine|SecE]]

**TCB must be monitored to ensure it is trustworthy**
- fingerprint and authenticate TCB code, meaning to digital sign the TCB code and monitor its **integrity** and therefore **authenticity**
- monitor the execution
- protect the code

[[hardware/hardware-based security/software measurement|software measurement]]

# key
The entire security of the system is derived from a [[hardware/hardware trust/_hardware trust|root of trust]], which is a **secret cryptography key** $K_R$ only accessible to TCB components

The key **must be unique** for each single piece of hardware
It can be:
- **burned in** at the factory by the manufacturer, implying trust issues with the manufacturer and [[hardware/_intro/supplies chain|supplies chain]]
- use [[hardware/PUFs/_PUFs - Physically Unclonable Functions|PUFs - Physically Unclonable Functions]] to derive the keys



From the $K_R$ are generated signing and verification keys:
- **public key**, (KPK, key production key) for encrypting data to be sent to the processor
- **signature verification key** $K_{VK}$ for checking the data signed by the processor


with an embedded signing key, the software running in the [[hardware/hardware-based security/TEE - trusted execution environment|TEE]] can be measured to attest to external users what cose is running

[[hardware/hardware-based security/software measurement|software measurement]]

