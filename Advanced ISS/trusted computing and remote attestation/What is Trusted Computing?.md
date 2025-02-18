**Trusted Computing**

A **trusted component** or **trusted platform** is one that consistently behaves as expected. This does not guarantee absolute security or correctness but means there has been no alteration from the initial programming. If a program contains an inherent bug, a trusted system implies that this bug originates from the programmer rather than any external interference.

To validate the expected behavior of a system, **attestation** is used. Attestation generates evidence of the platform’s current state—particularly the software state, encompassing active applications and configurations—that can be verified externally.

A reliable foundation in Trusted Computing is the **Root of Trust (RoT)**, which acts as the starting point for verifying system integrity. The RoT might be embedded in a microcontroller or within firmware performing self-verification. Building from this trusted base, the system can verify each subsequent component's integrity in a secure boot process.

The Trusted Computing approach defines schemas for establishing trust in a platform by identifying its hardware and software components.

A significant tool in this approach is the **Trusted Platform Module (TPM)**. The TPM provides methods for collecting and reporting system identities, establishing that the platform is in a known and expected state. A TPM does not stop system operations but instead acts as a **Trusted Reporter** that provides undeniable evidence of the system’s state. By verifying the reported state against expected behavior, trust in the platform can be established.
