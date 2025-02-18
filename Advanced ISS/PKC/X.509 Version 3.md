---
aliases:
  - x.509v3
---
### X.509 Version 3

To resolve the issues of earlier versions, **X.509 version 3** was developed in collaboration with the **IETF** and finalized in **June 1996**. By that time, it was clear that **OSI** would not succeed, and this version was tailored for **internet applications**. The X.509 v3 standard unified all necessary modifications to extend the definition of certificates and **Certificate Revocation Lists (CRLs)**.

#### Extensions in X.509 v3

There are two types of extensions in **X.509 v3**:

- [[Advanced ISS/PKC/Public Extensions|Public Extensions]]: These are pre-defined in the standard, and all parties should be aware of them. They are universally recognized and understood.
  
- [[Advanced ISS/PKC/Private Extensions|Private Extensions]]: These allow the creation of custom extensions for specific groups or purposes. For instance, at the **Politecnico di Torino**, a private extension was used to store student IDs inside certificates until a public extension became available. Private extensions offer great flexibility but may lead to issues since they are only understood by the specific group that defines them.

#### Certificate Profile

With the introduction of extensions, the concept of a **certificate profile** emerged. A certificate profile specifies which extensions should be used for a particular purpose. For example, **RFC-5280** provides the profile for **Internet applications**, defining the required extensions and values for **Public Key Certificates** and **CRLs** in these environments. A profile selects a subset of the general X.509 v3 standard for specific use cases, such as **email security** in **TCP/IP**.

#### Certificate Structure

X.509 v3 certificates are defined using **ASN.1** (Abstract Syntax Notation 1). This is the notation used to describe certificates and CRLs. The symbol "`::=`" is used for definitions, much like **structs** in the **C programming language**.

A **certificate** is a **sequence** of fields, typically:

- **signatureAlgorithm**: Identifier for the algorithm used.
- **tbsCertificate**: (To be signed Certificate) The core certificate data.
- **signatureValue**: The actual signature, stored as a bit string.

#### TBSCertificate Fields

The **TBSCertificate** (To Be Signed Certificate) is a sequence of fields and contains:

- **version**: Indicates the version of the certificate (`0` = v1, `1` = v2, `2` = v3).
- **serialNumber**: A unique number identifying the certificate.
- **signature**: Identifies the algorithm used for signing, not the signature itself.
- **issuer**: The entity that created and signed the certificate.
- **validity**: Specifies the start and end dates of the certificate's validity.
- **subject**: The entity controlling the private key corresponding to the public key in the certificate.
- **subjectPublicKeyInfo**: Contains the public key.
- **issuerUniqueID** and **subjectUniqueID**: Unique identifiers for the issuer and subject, though rarely used.
- **extensions**: The main feature of X.509 v3, enabling flexible and customizable certificates. Without this field, the certificate would be an X.509 v1 certificate.

