---
aliases:
  - CA
  - RA
  - VA
---
It is composed by:

- **Certification Authority (CA)**: it is the actor of the system which is in charge of *generating* and *revoking* Public Key Certificates. The CA also publishes PKCs and the information about their status (e.g. CRL). The CA can be the only actor in the Certification Architecture, but often it is supported by one or more RAs.
  
- **Registration Authority (RA)**: the actor that *verifies* claimed identity and attributes, thus *authorizing* PKC issuing/revocation.

- **Validation Authority (VA)**: it could be external, and it is the actor who provides services to verify the validity status of a PKC. This could also be done by the CA itself.

- **Revocation Authority (unofficial term, role can be assigned to RA or CA)**: revocation can be more urgent than issuing. Consider a scenario where a private key has been stolen at 3:00 AM, and that key might be used to access a bank account—it needs to be blocked immediately. If the CA is closed during the night, it would not be possible to revoke the certificate at that time. An office that is always open and ready to perform such operations is needed.

The CA must always be present, while the other roles exist to provide support.
