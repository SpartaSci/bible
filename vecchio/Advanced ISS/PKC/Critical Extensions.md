

Every time an extension is written, it can be defined as **critical** or **non-critical**. There is always someone using the certificate to protect transactions, and someone accepting the certificate. The acceptor (later referred to as the **Relying Party (RP)**—the one relying on the certificate for security) has a duty: it must perform verification.

If, during the verification process, the acceptor detects that the certificate contains an extension marked as "critical" and it is unrecognized, then it **must reject the certificate**. 

**Example**: If I receive the certificate and there is something I don’t understand that is marked as critical, I discard the certificate and close the transaction. 

On the other hand, if the extension is marked as **non-critical** and is not understandable, it may be ignored (though I could still decide to reject it if I am being very strict).

For instance, let’s imagine that a certificate contains a photo of the person. That photo should be marked as non-critical since it may be useful if the individual is in front of you, but not during an internet transaction. However, it is possible to specify that the photo must always be present, and in its absence, the certificate can be rejected.

This different processing is entirely the responsibility of the entity performing the verification: the **Relying Party (RP)**.
