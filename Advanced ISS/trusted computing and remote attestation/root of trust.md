---
aliases:
  - RoT
---


The **Root of Trust (RoT)** is a critical component that must consistently behave as expected, as any deviation cannot be detected. It serves as the foundation for establishing trust within a platform, and it typically combines hardware components with supporting software. Different types of RoTs are employed in a trusted computing environment to ensure system integrity:

- **Root of Trust for Measurement (RTM)**: The RTM is responsible for computing values that assess the system's integrity. Typically, the CPU runs the Core Root of Trust for Measurement (CRTM), a software component that performs these measurements and relays them to another RoT (the RTS). 

- **Root of Trust for Storage (RTS)**: The RTS provides a secure or shielded portion of memory where integrity measurements are stored. This shielded memory ensures that only the CRTM can modify its contents, protecting it from unauthorized changes.

- **Root of Trust for Reporting (RTR)**: The RTR is responsible for securely reporting the content of the RTS to external verifiers. 

The sequence in Trusted Computing begins with the **RTM** performing measurements, which are stored in the **RTS** and later accessed by the **RTR** when needed. This process allows external verifiers to confirm the platform's integrity based on recorded measures.

The **Trusted Platform Module (TPM)** often functions as both the RTS and RTR, providing secure storage and trusted reporting. The CRTM complements the TPM, especially when paired with secure boot. The secure boot verifies the proper installation of the CRTM, which then continuously measures system integrity and stores results securely in the TPM, facilitating reliable reporting.
