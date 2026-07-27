---
tags:
  - hardware
aliases:
  - root of trust
---
 

> a **trusted component, operation, or process** is one whose behavior is **predictable** under almost any operating condition and is highly **resistant** to sabotage by application software, virus, and given level or physical interference

# hardware trust anchor
>is a component that securely store and provide a unique secure identifier for the device


# root of trust
 
>component that needs to always behave in the expected manner because its misbehaviour cannot be detected


the execution has an expected behaviour and that expected behaviour can be used to build on top

it is used as basic block for the construction of a **chain of trust**

## for measurement RTM
initiates process of recording what software is running  [[hardware/hardware trust/CRTM - Core Root of Trust for Measurement|CRTM - Core Root of Trust for Measurement]]
implement in an immutable or securely updateable component 
[[hardware/hardware trust/TPM features/secure boot|secure boot]] [[hardware/hardware-based security/software measurement|software measurement]]


## for storage RTS
implements shielded locations like registers with special integrity or confidentiality
Implemented in a [[hardware/hardware trust/TPM - Trusted Platform Module|Trusted Platform Module]]
## for reporting RTR
uses cryptography to give assurances to third parties
Built from keys burned into [[hardware/hardware trust/TPM - Trusted Platform Module|TPM]] at manufacture time


# built-in security features

[[hardware/hardware trust/modern architecture built in security features|modern architecture built in security features]]

