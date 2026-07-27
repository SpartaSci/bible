---
tags:
  - hardware
aliases:
  - TPM
---

>A TPM, or a trusted platform module, is a physical or embedded security technology (micro-controller) that resides on a computer’s motherboard or in its processor.

%%standard guideline for developing TPM is based on different [[hardware/hardware trust/_hardware trust#root of trust|root of trust]] components and well-defined interactions among them%%



provides hardware-based [[cybersec/_properties/authentication|authentication]], [[cybersec/_properties/integrity|integrity]] and attestation to the [[hardware/hardware-based security/TCB - trusted computing base|TCB]]

it is designed as a small [[hardware/_intro/Tamper-resistant devices|Tamper-resistant]] *(anti-manomissione)* chip that provides the following functions:
- a [[hardware/hardware trust/_hardware trust#root of trust|root-of-trust]] for [[hardware/hardware trust/_hardware trust#for reporting RTR|reporting]] and [[hardware/hardware trust/_hardware trust#for storage RTS|storage]] 
- [[hardware/hardware-based security/software measurement|measurement]] and attestation of platform integrity
- platform identification and authentication
- core and highly constrained cryptographic functions
# type
- **discrete** (most common and secure)
- integrated
- firmware
- software
- virtual/hypervisor
# architecture
1. **storage**, persistent or versatile memory, to store various type of keys and configurations
2. **Cryptographic processor**
	1. random number generation [[hardware/random number generator/_random number generator|RNG]]
	2. cryptographic function and processing
		1. RSA key generator
		2. Hash generator
		3. enc-dec engine
![](https://upload.wikimedia.org/wikipedia/commons/b/be/TPM.svg)

# feature 
[[hardware/hardware trust/TPM features/secure boot|secure boot and firmware integrity]]
[[hardware/hardware trust/TPM features/Certification|Certification]]
[[hardware/hardware trust/TPM features/Attestation and Authentication|Attestation and Authentication]]
[[hardware/hardware trust/TPM features/Protected Location|Protected Location]]
[[hardware/hardware trust/TPM features/Integrity measurements and reporting|Integrity measurements and reporting]]


