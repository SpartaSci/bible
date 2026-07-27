[[hardware/hardware trust/TPM - Trusted Platform Module|TPM]]
# TPM 1.2 Overview

Trusted Platform Module (TPM) 1.2 is a secure hardware component historically popular in computing for verifying system integrity and protecting sensitive data. However, it has some limitations in flexibility compared to its successor, TPM 2.0.

## Core Attributes of TPM 1.2

TPM 1.2 has a fixed design:
- **Algorithms**: Uses SHA-1 for hashing and RSA for key generation, encryption, and signature verification.
- **Storage**: Has a single storage hierarchy for the platform user, with one **Storage Root Key (SRK)** (RSA-2048) as the base of secure data storage.
- **Endorsement Key (EK)**: Each TPM contains a unique EK, providing the platform with a hardware identity.
- **Sealing and Platform Configuration Registers (PCRs)**: Sealing of data (locking access to certain system states) is tied to **PCR** values, which record the platform's state.

## Components and Functions in TPM 1.2

The TPM 1.2 consists of the following main elements:
- **Random Number Generator**: Supplies secure random numbers for cryptographic processes.
- **RSA Key Generator and Encryption Engine**: Handles key creation and cryptographic functions, such as signing and encrypting data.
- **Secure Memory**: Stores essential keys, like the **Endorsement Key** and **Storage Root Key**, within a tamper-resistant area.
- **Platform Configuration Registers (PCRs)**: Record the system configuration, allowing for system integrity checks.
- **Attestation Identity Keys (AIKs)**: Used for signing reports during **remote attestation**, which securely verifies system state to an external party.

Overall, TPM 1.2 offers solid, though somewhat rigid, functionality focused on system integrity and secure data storage. It provides essential security functions but lacks the flexible configuration options seen in TPM 2.0.


![](https://upload.wikimedia.org/wikipedia/commons/b/be/TPM.svg)