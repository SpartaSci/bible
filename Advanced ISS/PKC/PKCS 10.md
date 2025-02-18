### PKCS#10

PKCS#10 is the most widely used method for certificate requests, documented in **RFC-2986**. It is also referred to as a **CSR (Certificate Signing Request)**. The request contains the distinguished name (the desired identifier), the public key, and optionally other attributes.

Some important attributes include the **challenge password**, which is a one-time code given by the registration authority and is useful for registration and revocation. If someone’s private key is stolen, they may need to request a revocation, but the CA could be located far from the victim. To prove ownership of the certificate, the victim can use the special code provided at the time of the certificate's creation for revocation. Other attributes or information about the requestor may also be included.

The schema includes the data to be certified: the **distinguished name (DN)**, the public key, and the attributes. These elements are placed in the first part of the PKCS#10 request. Since **Proof of Possession (POP)** is required, the private key is used to sign the data to be certified, and the signature is included in the second part of the PKCS#10 request.

When the CA receives the signed data, it verifies the signature using the public key. This process demonstrates that the user controls the private key corresponding to the public key, and then the CA issues the certificate. 

This approach, which involves POP at the moment of the request through signing the data, is the most common method used today.
