
Attackers often aim to inject malware at the lowest possible level of a system to avoid detection and gain control over as much of the system as possible. Their strategies include modifying the operating system, attempting to boot an alternative OS, or tampering with the boot sequence or boot loader.

To counter these threats, we must protect both the boot system and the OS. In the past, systems relied on the **Basic Input Output System (BIOS)**, which was responsible for controlling physical devices during the boot phase. However, BIOS was invented in the 1980s when security wasn’t a significant concern, making it difficult to protect effectively.

Nowadays, we use the **Unified Extensible Firmware Interface (UEFI)**, which is not only found on modern computers but also on servers. UEFI extends BIOS for backward compatibility while adding native support for **firmware signature** and **verification**. When a system boots, UEFI verifies the correctness of its signature before execution, ensuring the firmware hasn't been tampered with.

After UEFI, the boot loader verifies the OS's integrity before launching it. If the UEFI signature is valid, it confirms that the boot loader hasn't been altered. This process creates a **root of trust**, establishing a secure chain from UEFI to the boot loader and finally to the OS.
