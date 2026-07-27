---
aliases:
---

Rootkits are malicious software designed to gain unauthorized access by modifying core system components, allowing them to execute before or alongside the operating system. They come in various forms, each targeting different parts of the system:

- **Firmware Rootkits**: Overwrite the BIOS/UEFI or the firmware of other hardware, allowing the rootkit to start before the operating system.
  
- **Bootkits**: Replace the OS's bootloader, ensuring that the bootkit loads before the operating system.

- **Kernel Rootkits**: Modify a portion of the OS kernel, enabling the rootkit to automatically run when the operating system starts.

- **Driver Rootkits**: Masquerade as trusted drivers used by the OS (e.g., Windows) to communicate with hardware, giving the rootkit control at a lower system level.
