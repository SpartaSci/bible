

In addition to, or in substitution of, **keyUsage** (which specifies cryptographic operations), the **Extended Key Usage (EKU)** field defines the application purposes for which a certificate can be used. Both **keyUsage** and **EKU** can coexist, but in case of conflicts, one must take priority. Some possible values are:

- **(id-pkix.3.1) serverAuth [DS, KE, KA]**
  - Server authentication, like the one in TLS.
  - Compatibility with **keyUsage**: **Digital Signature (DS)**, **Key Encryption (KE)**, and **Key Agreement (KA)**.
  - Used for certificates required for web servers.
  
- **(id-pkix.3.2) clientAuth [DS, KA]**
  - Used for client authentication in TLS.
  - Compatibility with **keyUsage**: **Digital Signature (DS)** and **Key Agreement (KA)** (KE is not needed for the client).
  
- **(id-pkix.3.3) codeSigning [DS]**
  - Ensures the integrity and origin of software by digitally signing the code.
  
- **(id-pkix.3.4) emailProtection [DS, NR, KE, KA]**
  - Protects email messages by ensuring integrity, authenticity, and optionally encryption.
  - Compatibility: **Digital Signature (DS)**, **Non-Repudiation (NR)**, **Key Encryption (KE)**, and **Key Agreement (KA)**.

- **(id-pkix.3.8) timeStamping [DS, NR]**
  - Attaches a trusted timestamp to a document.
  - Compatibility: **Digital Signature (DS)** and **Non-Repudiation (NR)**.

- **(id-pkix.3.9) ocspSigning [DS, NR]**
  - Used for signing OCSP responses.
  - Compatibility: **Digital Signature (DS)** and **Non-Repudiation (NR)**.

> **Note**: Non-repudiation (NR) is typically linked to actions performed voluntarily by a human. However, in cases like timeStamping and ocspSigning, NR is used to ensure accountability, meaning the server operator is responsible for verifying the status of certificates.
