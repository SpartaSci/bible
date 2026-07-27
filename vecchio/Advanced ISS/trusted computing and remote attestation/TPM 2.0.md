# TPM 2.0 Overview

TPM 2.0 represents a significant advancement over its predecessor, TPM 1.2, by introducing cryptographic agility and flexibility in key management, making it suitable for a broader range of applications, including mobile and automotive environments.

## Key Features of TPM 2.0

1. **Cryptographic Agility**: 
   - Supports both SHA-1 and SHA-256 hash algorithms.
   - Provides RSA for backward compatibility and adds support for ECC (Elliptic Curve Cryptography) with ECC-256.
   - Includes native features like HMAC based on SHA-1 or SHA-256.
   - Supports AES-128 encryption, with additional optional algorithms.

2. **Key Hierarchies**:
   - **Platform Hierarchy**: For data coming from the external platform.
   - **Storage Hierarchy**: For internal storage of keys and sensitive data.
   - **Endorsement Hierarchy**: For providing information to external entities.
   - Each hierarchy can have multiple keys and utilize various algorithms.

3. **Policy-Based Authorization**:
   - TPM 2.0 allows for more complex access controls, including multiple passwords, two-factor authentication, or biometric methods.
   - This enhances security compared to the single-password model of TPM 1.2.

4. **Platform-Specific Specifications**:
   - TPM 2.0 includes specifications for different platforms, such as PC clients, mobile devices, and automotive systems, ensuring trust is prioritized in diverse environments.

## Implementations of TPM 2.0

TPM 2.0 can be implemented in several forms, each offering different security characteristics:

- **Discrete TPM**: 
  - A dedicated chip that implements TPM functionality in its own tamper-resistant package (e.g., manufacturers like STM and Infineon).

- **Integrated TPM**: 
  - The TPM is embedded as part of another chip, such as Intel's chipsets. In this case, tamper resistance is not guaranteed.

- **Firmware TPM**: 
  - A software-only solution that runs the TPM firmware within a CPU’s Trusted Execution Environment (TEE). Companies like AMD, Intel, and Qualcomm have developed firmware TPM solutions.

- **Hypervisor TPM**: 
  - A virtual TPM provided by a hypervisor, running in an isolated execution environment. The security is comparable to a firmware TPM, but with potential vulnerabilities.

- **Software TPM**: 
  - A software emulator of TPM that runs in user space. It is primarily useful for development purposes and lacks real security.

## Implications for Trusted Computing Base (TCB)

Each implementation of TPM 2.0 leads to different characteristics in the Trusted Computing Base (TCB):

- **Discrete TPM**: Features a separate hardware RoT, providing robust security.
- **Integrated TPM**: Relies on the trustworthiness of the host chip (e.g., Intel) to ensure the integrity of the TPM.
- **Firmware TPM**: Requires trust in the software running the secure boot process.
- **Hypervisor TPM**: Involves additional uncertainty, as users may not be aware of the operations happening below the virtual machine.

Ultimately, the choice of TPM implementation depends on the acceptable level of trust in the underlying TCB.
