

While **ARM TrustZone** provides a foundational security architecture, it is limited by allowing only one secure enclave. To address this limitation, several companies have developed solutions:

- **Gemalto** created the **Trusted Foundations** system.
- **G+D (Giesecke+Devrient)** developed **MobiCore**.
  - Both systems effectively split the single secure enclave into multiple enclaves, utilizing a smart-card operating system.

### Trustonic Development

- Trustonic's development is based on **MobiCore**, enhancing the capabilities of ARM TrustZone.
- To implement Trustonic's code, license fees are required.

### Trustonic's TEE OS

- Trustonic offers the **TEE OS** known as **Kinibi**.
  - For example, **version 500** includes support for **64-bit Symmetrical Multi Processing (SMP)**, tailored for embedded systems.

### Comparison with Samsung Knox

- **Samsung Knox** is a similar solution that also introduces **secure boot** features, further enhancing the security of mobile devices.
