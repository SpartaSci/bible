

### **Plain Boot**
- **No security** is applied during the boot process.

### **Secure Boot**
- The **firmware verifies the signature** of each piece of boot software, including UEFI firmware drivers and the OS.
- The platform will halt if the verification fails.
- **Hardware-based** security that verifies up to the OS-loader.
- It’s a **feature of the hardware**.

### **Trusted Boot**
- The **OS verifies the signature** of OS components such as drivers and anti-malware software.
- Operations stop if the verification fails.
  - **Note**: Signature verification does not guarantee that components are trustworthy (e.g., malware like **Stuxnet** disguised itself as a Windows driver with a valid digital signature).
- **Software-based** security that verifies up to the OS operational state.
- It’s a **feature of the OS**, not the firmware.

### **Measured Boot**
- **Measures all components** executed from boot up to a specific point.
  - Measuring typically means **computing the digest** of every piece of software being executed, starting from the firmware.
- **Does not stop operations** but securely reports measurements to an external verifier.
  - Reports are sent using **remote attestation**.
  - Since it doesn’t halt operations, it’s not a self-contained security mechanism.
- **Specific to certain hardware-firmware pairings**.

> **Note**: These boot mechanisms can be implemented together to achieve a higher level of security.
