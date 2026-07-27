---
tags:
  - hardware
  - authentication
---
> root of trust components are usually the entities trusted when attesting a devices

**Unique** **identifiers** can be **stored** in a [[hardware/hardware trust/_hardware trust#|root of trust]] element and used to identify the system

A unique identifier can be obtained by resorting to [[hardware/PUFs/_PUFs - Physically Unclonable Functions|Physically Unclonable Functions]] PUFs

Trusted platforms employ a **hierarchy** of attestation, that takes the form of keys, certificates, software signature, etc. that are stored inside the [[hardware/hardware trust/TPM - Trusted Platform Module|TPM]]

