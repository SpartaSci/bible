
Intel Identity Protection Technology (IPT) offers an alternative approach to remote attestation (RA) for containers, specifically utilizing normal CPUs. This technology provides a secure method for authentication and data protection.

**Separate Processor**: Intel IPT operates by running a Java applet on a **secondary processor**, which is dedicated to Intel. This secondary processor is integrated into the **Management Engine (ME)**, a component of the chipset that is bound to the physical hardware, enhancing security.

### Sample Applications

Intel IPT supports various applications that leverage its secure capabilities:

- **Key Generation and Storage**: 
  - Keys can be generated either entirely in software or with the assistance of Intel IPT. This process can be integrated with drivers that support systems like the **Windows Cryptographic API**.

- **One-Time Password (OTP) Generation**: 
  - Applications such as **VASCO MYDIGIPASS.COM** utilize Intel IPT to generate OTPs securely. The OTP can be created within the dedicated processor, ensuring secure authentication.

- **Secure PIN Entry**: 
  - Intel IPT allows for secure PIN entry by managing the video output through the chipset. For instance, the touch screen can be connected to the Management Engine for specific operations, like entering a PIN, ensuring that sensitive information is securely handled during input.

