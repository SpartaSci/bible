---
tags:
  - hardware
  - integrity
  - authenticity
aliases:
  - trusted boot
  - secure boot
  - authenticated boot
---
>The environment in which the codes runs must be **controlled**. **Secure boot** is the act of establishing a secure initial state.


The typical secure boot method verifies the authenticity of each **component** in the **boot chain** relying on [[hardware/hardware-based security/software measurement|software measurement]]

In the secure boot, we prevent the load of drivers and OS that are not signed with an acceptable digital signature.

![](https://www.lffl.org/wp-content/uploads/2020/10/chain-of-trust.png)


The first boot sequence start after the BIOS process.
[[hardware/hardware-based security/secure engine|SecE]]

A first **protected** bootloader (A), stored in a **secure memory**, verifies the #integrity and #authenticity of a second bootloader (B)
The second bootloader (B) verifies the integrity and authenticity of the Operating System kernel and of the firmware

Typically, the A **cannot** be modified, whereas the B can be update.






