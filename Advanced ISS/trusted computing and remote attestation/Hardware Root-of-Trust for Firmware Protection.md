

Firmware protection can also rely on an external hardware component to ensure higher security, rather than self-verification by the firmware itself.

- **Self-Verification**: 
  - The **dynamic part** of the boot ROM can be updated, while the **static part** remains unchanged. The static part verifies the dynamic part's integrity and authenticity.
  
- **External Chip Verification**: 
  - Firmware verification can also be performed by an **external crypto chip**, which acts as a hardware root-of-trust (RoT).

- **Crypto Micro Controller**:
  - Performs cryptographic operations using dedicated hardware.
  - Can decide whether the BIOS should be available or not, based on validation results.

- **Validation Process**:
  - After **power on**, the external crypto chip validates the BIOS stored in the **SPI flash**.
  - This process is similar to the BIOS self-integrity check, but with the external chip performing the validation instead of the CPU. This enhances security by avoiding self-verification.

- **CPU Reset**:
  - Only after successful validation does the x86 CPU come out of reset. If the validation fails, the CPU remains in a reset state.

- **Public Key Storage**:
  - The **public key** used to verify the signature of the hash file stored in the BIOS signature region can be **fused into the hardware** of the crypto chip.
  - Storing the key directly in the chip ensures higher security than reading it from external storage.
  - The fusion process is one-time only, meaning if the **private key** is lost, the chip becomes unusable, emphasizing the need for strong protection of the private key.
