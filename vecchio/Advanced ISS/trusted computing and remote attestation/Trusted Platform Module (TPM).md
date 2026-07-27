
A Trusted Platform Module (TPM) is a small, cost-effective, tamper-resistant component (typically under $1) found in most servers, laptops, and PCs. Though not tamper-proof, the TPM resists tampering attempts and provides a foundational layer of security, achieving the Common Criteria EAL4+ certification—a relatively high assurance level. 

The TPM is a passive component, meaning it does not control the computer but is directed by the CPU, making it suitable for data protection rather than enforcing boot controls.

## TPM Features
- RTS - secure storage (extedn-only)
- RTR - report content of RTS with digital signature.
- **Random Number Generation**: The TPM includes a hardware-based random number generator, providing high-entropy, true random values (not a pseudo-random generator).
- cyrpto algorithm but it's not a crypto accelerator (slow!)
  
- **Secure Key Generation**: Generates cryptographic keys for specific, limited purposes, ensuring these keys are not reused for unintended applications.
  
- **Remote Attestation**: Stores a cryptographic hash of the system’s hardware and software configuration. This hash can be verified by a third party to ensure the system remains unchanged from a known secure state.
  
- **Binding**: Encrypts data using a unique RSA bind key, specific to that TPM. Bound data cannot be decrypted outside of the originating TPM, providing strong data security—even in cases of data theft. However, this requires a complex process if data needs to be moved to a new machine.
  
- **Sealing**: Adds a layer of conditional security, where encrypted data can only be decrypted if the system state matches its original encryption state. The TPM checks that all previously known applications and configurations are still active and intact. If the state has changed, decryption is denied.

- **Device Authentication**: Uses a unique Endorsement Key (EK) embedded at production, allowing device identification. This EK enables machine authentication, which can be valuable for asset tracking, though it requires careful privacy considerations to ensure authorized use only.
