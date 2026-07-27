

**Keystone** is an open-source framework designed for building a Trusted Execution Environment (TEE) that allows for customization and flexibility.

### Key Features

- **Selective Feature Selection**: 
  - Users can select only the necessary features, which helps avoid overloading systems with limited computational capabilities.

- **Minimized Trusted Computing Base (TCB)**: 
  - By minimizing the TCB, Keystone enhances resistance to attacks, as a smaller attack surface is less vulnerable.

- **Environment Structure**: 
  - Keystone operates within an untrusted environment (general-purpose OS) while supporting multiple trusted segregated enclaves.

### Hardware Basis

- Built on **RISC-V** open-source customizable hardware, Keystone can utilize:
  - **FPGA** (Field Programmable Gate Array) or **SoC** (System on Chip).
  - **Core and Crypto Extensions** for added functionality.
  
- **Execution Modes**:
  - Supports various execution modes, including **Machine (M)**, **Supervisor (S)**, and **User (U)**, where M has the highest privilege and U has the lowest.

- **Physical Memory Protection (PMP)**:
  - Usable for memory management to segregate enclaves and for I/O control, ensuring that specific I/O devices can only be accessed by designated enclaves at specific times.

## Motivation for Keystone

- **Lack of Customizability in Existing TEEs**:
  - Current solutions like ARM TrustZone, Intel SGX, and AMD SEV are closed proprietary environments, making them rigid and difficult to modify. For instance, Intel SGX requires a formal agreement with Intel to certify keys for attestation, complicating the process.

- **Design Limitations of Existing Solutions**:
  - [[Advanced ISS/TEE/Intel SGX|Intel SGX]]: Has a large software stack.
  - **AMD SEV**: Features a large TCB.
  - [[Advanced ISS/TEE/ARM TrustZone|ARM TrustZone]]: Lacks sufficient domains for varied applications.

# Keystone Architecture

Keystone is designed to create a secure framework with a clear separation between trusted and untrusted environments.

The **Security Monitor (SM)** operates in **M-mode**. It is not a full operating system; instead, it checks whether requested operations align with security policies, ensuring that specific keys or devices are used only by authorized applications.

The **general-purpose operating system**, which is considered untrusted, runs in **S-mode**. In the trusted environment, a minimized operating system called the **Runtime (RT)** also runs in S-mode. The RT is a modified version of Linux that contains only the essential components necessary to execute applications securely.

Both untrusted applications and trusted enclave applications run in **U-mode**. Each enclave has its own U-mode, allowing Keystone to support multiple enclaves simultaneously.

![](https://d3i71xaburhd42.cloudfront.net/57dfe28cc9347da343468879fbac5192f40fc847/2-Figure1-1.png)




# Keystone: further references
Keystone presentation at CCC:
https://www.youtube.com/watch?v=ITA3FfjKqNk;

Keystone presentation at EuroSys’20:
- https://www.youtube.com/watch?v=S8MmKBCoPSg;
- https://n.ethz.ch/~sshivaji/publications/keystone_eurosys20.pdf;