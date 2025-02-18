[[hardware/hardware-based security/TCB - trusted computing base|TCB]]


The **Trusted Computing Base (TCB)** is the collection of a system’s hardware and software resources that ensure the enforcement of its security policy. A critical aspect of the TCB is that it must remain self-protected, meaning it cannot be compromised by any external hardware or software. For instance, the crypto microcontroller previously mentioned is part of the TCB and could only be compromised by itself, such as through a production error.

The **Trusted Platform Module (TPM)**, however, is not part of the TCB. Rather, the TPM serves as a tool to allow external entities to verify whether the TCB has been compromised. In some cases, the TPM can also prevent the system from starting if it determines that the TCB cannot be properly instantiated.
