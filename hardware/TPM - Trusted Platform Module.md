---
tags:
  - hardware
aliases:
  - TPM
---

> standard guideline for developing chips with strong cybersecurity features 
> Trustworthiness of TPM is based on different [[hardware/security/hardware trust#root of trust|root of trust]] components and well-defined interactions among them



provides hardware-based #authentication, #integrity and attestation to the [[hardware/TCB - trusted computing base|TCB]]

it is designed as a small tamper-resistant *(anti-manomissione)* chip that provides the following functions:
- a [[hardware/security/hardware trust#root of trust|root-of-trust]] for [[hardware/security/hardware trust#for reporting|reporting]] and [[hardware/security/hardware trust#for storage|storage]] 
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
[[secure boot & firmware integrity]]
[[certification]]
[[attestation and authentication]]
[[hardware/Protected Location|protected location]]
[[hardware/integrity measurements and reporting|integrity measurements and reporting]]
