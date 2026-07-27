
**Intel Software Guard Extensions (SGX)** is a security feature tightly integrated with Intel CPUs, enhancing hardware memory management. 

### Key Features

- **Memory Isolation**: SGX modifies the hardware memory management system to create separate pages that are completely isolated from the operating system and other processes.
  
- **Enclave Protection**: 
  - Enclaves are protected from external code, ensuring that an enclave can only access a specific memory page.
  - When an enclave is inactive, its memory page is encrypted, making it inaccessible even to users with root privileges.

- **Code Measurement**: 
  - As enclaves are created, the code within them is measured in a manner similar to a Trusted Platform Module (TPM).
  - A significant limitation of SGX is that when an enclave is running, it is not possible to know what is occurring inside it.

### Integration with Other Technologies

- SGX can be combined with **Intel Identity Protection Technology (IPT)** to enable trusted display functionalities.

### Version Availability

- Initially, **SGX1** was available on both low and high-end CPUs. Currently, **SGX2** is primarily restricted to server-oriented CPUs, specifically **Xeon** processors.
