[[Advanced ISS/PKC/Public Extensions|Public Extensions]]

The first class contains 6 extensions, listed as follows:

- **Authority Key Identifier (AKI)**: 
  Any actor may have more than one key pair, and if it has more than one, it may need a way to distinguish them: "To which certificate is this key pair associated?" This is the purpose of the AKI, which identifies a specific public key used to sign a certificate. The identification is typically performed by means of a key identifier, usually the digest of the PK (public key) computed with a suitable hash algorithm, or by the pair `issuerName:serialNumber`. AKI is **non-critical**, but its omission can cause issues since many software applications rely on it to build the certificate chain.
  
- **Subject Key Identifier (SKI)**: 
  This is either a digest or a pair `issuerName:serialNumber` to identify a specific public key used in an application (e.g., when a public key is updated). It refers to the public key of the subject and is **non-critical**. Although it can be omitted, it is often computed alongside the AKI.

- **Key Usage (KU)**: 
  It identifies the application domain for which the public key can be used (e.g., signature, encryption). It can be **critical** or **non-critical**, depending on the CA. Some values for the KU extension include:
  - `digitalSignature`: Can appear in both CA and user certificates.
  - `nonRepudiation`: Only for users, associated with legal obligations.
  - `keyEncipherment`: Used to encrypt a key with a public key, valid only for users.
  - `dataEncipherment`: Used to directly encrypt data with a key, valid for both users and CAs.
  - `keyAgreement`: Supports key agreements like Diffie-Hellman.
  - `keyCertSign`: Only for CAs, permission to sign a certificate.
  - `cRLSign`: Only for CAs, permission to sign a CRL.

- **Private Key Usage Period**: 
  Defines the validity period of the private key. It is **non-critical** and its usage is generally discouraged because it limits the user by imposing restrictions on key reuse. It can be useful in high-security environments to limit key lifetime for cryptanalysis protection.

- **Certificate Policies**: 
  Lists the policies followed when the certificate was issued and the purposes for which it can be used. The policies can be indicated as text, a URI, or an OID. It can be **critical** or **non-critical**, but is typically **non-critical** as it mostly provides context for certificate usage.

- **Policy Mappings**: 
  Indicates the correspondence (mapping) of policies among different certification domains (e.g., `CA1` follows policy `x`, which maps to policy `y` of `CA2`). It is present only in CA certificates and is typically **non-critical**.
