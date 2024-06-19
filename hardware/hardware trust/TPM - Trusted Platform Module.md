---
tags:
  - hardware
aliases:
  - TPM
---

> standard guideline for developing chips with strong cybersecurity features 
> Trustworthiness of TPM is based on different [[hardware/hardware trust/_hardware trust#root of trust|root of trust]] components and well-defined interactions among them



provides hardware-based #authentication, #integrity and attestation to the [[hardware/hardware-based security/TCB - trusted computing base|TCB]]

it is designed as a small tamper-resistant *(anti-manomissione)* chip that provides the following functions:
- a [[hardware/hardware trust/_hardware trust#root of trust|root-of-trust]] for [[hardware/hardware trust/_hardware trust#for reporting|reporting]] and [[hardware/hardware trust/_hardware trust#for storage|storage]] 
- measurement and attestation of platform integrity
- platform identification and authentication
- core and highly constrained cryptographic functions
# type
- discrete (most common and secure)
- integrated
- firmware
- software
- virtual/hypervisor
# architecture
storage, persistent or versatile memory 
random number generation
cryptographic function and processing
![](https://upload.wikimedia.org/wikipedia/commons/b/be/TPM.svg)
![](https://www.lffl.org/wp-content/uploads/2020/10/chain-of-trust.png)

# feature 
[[hardware/hardware-based security/secure boot]]
[[hardware/hardware trust/Certification]]
[[hardware/hardware trust/Attestation and Authentication]]
[[hardware/hardware trust/Protected Location|protected location]]
[[hardware/hardware trust/integrity measurements and reporting|integrity measurements and reporting]]
