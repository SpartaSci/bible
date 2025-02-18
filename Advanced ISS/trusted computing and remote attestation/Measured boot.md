# Measured Boot

To implement these capabilities, *measured boot* is performed instead of *secure boot*.

- The first stage of the boot loader, assumed to be trusted, constitutes the **core root for measurement**. This value is stored in the **Platform Configuration Register (PCR)**.
- The hash of the core root for measurement is verified (computed).
- The boot loader measures (computes the hash of) the second stage boot loader (UEFI/BIOS), then loads and executes it. The corresponding value is stored in the PCR through the **Extend Operation**.
- The second stage will store in the PCR `ℎ(𝑀1 || 𝑀2)`, which is the hash of *measure1* concatenated with *measure2*.
- The second stage boot loader first measures the operating system, loads it for execution, and performs an extension. After this step, there will be `ℎ(𝑀1 || 𝑀2 || 𝑀3)`. 

The PCR functions as an accumulator, not by simple summation, but by sequentially hashing previous hashes. The final value depends on all inserted hash values and their order.

Finally, the operating system can be modified to perform the same measurement sequence for applications:
- When an application is started, it is measured, loaded, and the value is extended into the PCR.  
- This step is optional. For example, **Windows** does not perform this, but **Linux** includes a special module that can.  
- Depending on the implementation, the PCR may contain a complete history of everything executed on the system from boot.  
- This represents the *state* of the system: when we refer to the system's state, we mean the sequence of applications executed.

An application may load and measure another application, continuing this process.

We mentioned modifying the OS to carry out these operations. Although it seems like modifying each application would be complex, this isn't necessary. Since applications start other applications using a specific **system call** (`exec`) within the kernel, only the OS needs modification, not every application.
