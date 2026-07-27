### Certificate Transparency (CT)

There is a whole organization of all the major providers that have joined together to create this specification, available at [Certificate Transparency](https://certificate-transparency.org/). This group aims to create an open, global auditing and monitoring system where:

- **Monitoring** means the ability to verify the current status of things whenever desired.
- **Auditing** means the ability to reconstruct what has happened in a system later on.

These operations should be based on public logs of issued certificates: all CAs are required to create these logs and permit public examination of them. This enables domain owners to verify that no fraudulent certificates have been issued for their domain. 

This means that the owner of a website, upon receiving a certificate that has been requested, can check if any other certificates have been issued in the name of the website owner, even if those were not requested, as this would indicate fraud. The domain owner should periodically perform this auditing operation to ensure that no unauthorized certificates exist.

Originally proposed by Google, this experimental protocol was later standardized by the IETF Public Notary Transparency Working Group. The purpose of this protocol is to allow the issuance and existence of TLS certificates (for web servers only) to be open to analysis by domain owners, CAs, and users. Anyone on the internet should be able to consult these logs, which is foundational for enhancing various software, especially web clients (browsers).

Browsers should only accept certificates that have been publicly logged; otherwise, there could be a fake CA or some entity circumventing the security measures of that specific CA. Conversely, it should be impossible for a CA to issue a certificate without it being publicly visible in the Transparency Log. This requirement is gradually being implemented.

This implies that every CA, including companies, should implement CT. For example, Verisign is a major CA that receives a CSR (Certificate Signing Request) and returns the certificate to the website. Verisign maintains a log that is publicly accessible. 

When a web browser receives the certificate from the website, it will check the log to see if the certificate has been logged. It's possible to create an internal CA (e.g., the CA of Politecnico di Torino) to generate certificates for internal TLS machines. However, if in the future there is no log for that specific CA, the browser may not connect to it.

This creates restrictions not only on official CAs but also on private ones. The point is that browsers will not accept a certificate unless it has been properly logged. Creating a CA is becoming increasingly complex; it involves not only properly issuing certificates and maintaining a revocation list but also complying with CT.

### Main Ideas of Certificate Transparency (CT)

The primary goal of Certificate Transparency (CT) is to make it impossible or very difficult for a Certificate Authority (CA) to issue a public key certificate (PKC) for a domain without making it visible to the domain owner. This involves:

1. **Mandatory Logging**: 
   - Internal procedures, both technical and manual, must include the creation of an entry in the log whenever a certificate is issued. If an entry is not created, the certificate should not be issued.

2. **Open Auditing and Monitoring Protocol**:
   - There should be a protocol for an open auditing and monitoring service that allows anyone to determine if a certificate has been issued mistakenly or fraudulently. Given the impracticality of reaching each CA physically, a protocol is essential.

3. **User Protection**:
   - The system aims to protect users from being provisioned with certificates that were mis-issued, particularly when a connection is established and a fake certificate is received.

### CT Actors

CT involves several participants beyond the web server and web client:

- **Submitters**: Entities that submit certificates to log servers.
- **Loggers**: Servers that maintain logs of issued certificates.
- **Monitors**: Entities that verify the behavior of log servers.
- **Auditors**: Entities that review logs to ensure compliance and integrity.

### CT – Log Servers

Every issued certificate is logged across multiple log servers worldwide, forming the core of the CT system. These public entities maintain a secure log of TLS certificates, with security ensured by:

- **Append-only**: 
  - Certificates can only be added to the log. They cannot be deleted, modified, or retroactively inserted.

- **Cryptographically Assured**: 
  - Instead of traditional digital signatures, the system uses **Merkle Tree Hashes**. This approach provides integrity and authentication without requiring a public key (PK) signature, preventing tampering and misbehavior.

- **Publicly Auditable**: 
  - Anyone can query a log using an HTTPS channel to verify that the log is behaving properly (no modifications, authenticity) and confirm that a TLS certificate has been legitimately appended.
### CT – Log Signature and Support

- **Digital Signatures for Logs**:
  - Logs must be digitally signed for integrity and authenticity.
    - **Version 1.0**: Supports NIST P-256 or RSA-2048.
    - **Version 2.0**: Supports NIST P-256, Deterministic ECDSA, or Ed25519.

- **Deterministic ECDSA**:
  - Refers to a method specified in **RFC-6979** ("Deterministic Usage of the DSA and ECDSA").
  - In this method, if the K value used in the computation is not random, the private key (SK) can be computed from the signature, posing a risk—particularly in embedded systems.

- **CT Support in Web Browsers**:
  - **Chrome/Chromium/Safari**:
    - Require 1 SCT from a currently approved log.
    - For durations < 180 days: require 2 SCTs from once-approved logs.
    - For durations > 180 days: require 3 SCTs from once-approved logs.
  
  - **Firefox**:
    - CT support is currently pending implementation.

### CT Operations

Anyone can submit a certificate to a log server, although most submissions will be made by CAs and server operators. Those who manage an internal CA could also create entries in a CT log. 

- **Signed Certificate Timestamp (SCT)**:
  - The logger promises to log the certificate within a certain timeframe, providing a Signed Certificate Timestamp (SCT). The SCT is a type of timestamp that is associated with the signature of the certificate and accompanies the certificate for its entire lifetime. Since the SCT is issued directly by log servers and not by CAs, it must be delivered with the certificate.


