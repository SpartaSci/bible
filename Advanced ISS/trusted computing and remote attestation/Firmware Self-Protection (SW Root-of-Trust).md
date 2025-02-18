

An example from **HPE (HP Enterprise)** demonstrates how firmware can protect itself through a software-based root-of-trust. HPE uses a signature region within the BIOS to ensure the integrity of the BIOS image.

- HPE reserves a **"signature" region** at a fixed location in the final 16MB BIOS image.
  
- After the BIOS is built (at the manufacturing stage), a **SHA256 hash** is calculated for specific BIOS regions. These include:
  - **Static code**, 
  - **BIOS version information**, and
  - **Microcode (µCode)**. 
    - The µCode consists of low-level CPU instructions stored in ROM and injected into the CPU before execution, making it a critical part of the system to monitor for integrity.

- The calculated hash is sent to the HPE **signing server**, which returns a signed hash image. This includes the hash (32 bytes) along with the signature and certificate. This signed data is copied into the BIOS "signature" region.

- Upon **power on**, the early BIOS code recalculates the combined hash for the specified valid regions of the BIOS image.

- The **stored hash** in the signature region is compared with the newly calculated hash.

- If the hashes match, the boot process continues. If they don't match, the system halts during the boot phase, preventing it from even reaching the operating system.
