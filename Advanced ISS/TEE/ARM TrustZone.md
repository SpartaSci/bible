

ARM TrustZone is a technology that enables the most advanced ARM processors to operate in two distinct zones: the **normal** (rich) environment and the **trusted** environment. This functionality is achieved by extending the CPU buses to support a virtual **33rd bit** for addressing.

### Secure Mode Indication

- The **33rd bit** serves as a signal to indicate whether **secure mode** is active. This signal is not confined to the CPU; it is exposed externally so that peripherals and RAM can also recognize when secure mode is in operation. 
- For instance, when a user enters their PIN using the smartphone's touch screen (a peripheral), the system ensures that no other applications can read the input if secure mode is active.
- Potentially could have indicator for which mode CPU is in;
### System Architecture

- ARM TrustZone is an **open system** and is well documented, but it supports only **one secure enclave**. 
  - While applications running in the TEE (Trusted Execution Environment) are isolated from those in the rich environment, they are **not protected from each other** since all run within the same enclave.

### Future Developments

- ARM is currently working on adding a **third mode** known as **"realm mode."** This new mode will enable the creation of secure **"realms"** (or enclaves) that are entirely separate from both the rich environment and the trusted environment, as well as from one another. This enhancement aims to provide more robust security and isolation for applications.
