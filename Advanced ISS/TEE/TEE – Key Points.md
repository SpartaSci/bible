
### TEE and Confidential Computing

In recent years, the **Trusted Execution Environment (TEE)** has become a crucial element in the field of **confidential computing**. This movement is driven by organizations like the **Confidential Computing Consortium (CCC)**, which focuses on protecting **"data in use"**—data that is actively processed, such as in the computer's **RAM** or in the **Cloud**.

- The goal is to ensure that no unauthorized party can read or write the data, even if they have the means or willingness to do so.
- Only **authorized applications** are allowed to process this sensitive data within the TEE, offering a higher degree of security compared to traditional methods.

This can be contrasted with cryptographic techniques used to secure **data at rest** (e.g., data stored on a disk) or **data in motion** (e.g., data being transmitted over a network), which don't necessarily protect data while it's being processed.

### Root of Trust (RoT)

A critical component within the TEE architecture is the **Root of Trust (RoT)**. This element must be both **trusted** and **trustworthy**, as any misbehavior on its part cannot be detected at runtime, making it a key security element. 

- The RoT is part of the **Trusted Computing Base (TCB)**, which consists of all hardware (HW), firmware (FW), and software (SW) components that are vital to the system’s overall security.
  - Any vulnerability within the **TCB** compromises the system, so minimizing the size of the TCB is crucial.
  - A **smaller TCB** reduces the attack surface, making it easier to thoroughly verify and secure.

By keeping the TCB as small and robust as possible, the system's overall security is improved, as there are fewer opportunities for attackers to exploit.
