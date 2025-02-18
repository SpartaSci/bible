---
aliases:
  - POP
---
When the CA creates a certificate, they should have some reasonable assurance that the requestor is controlling the corresponding private key. If there’s no such verification, problems arise because if a certificate is issued without checking the possession of the corresponding private key, there may be an issue with **non-repudiation**. While non-repudiation is not always critical for encryption, if non-repudiation is desired (and it is in any case involving a digital signature), then **Proof of Possession (POP)** is an important issue.

#### example
For example, there’s Alice with her own device and a CA that issues certificates without POP. Alice creates a private key and stores it locally, then sends a public key and an identifier to the CA. The CA verifies Alice’s identity and creates a certificate associating Alice to that public key. 

Now, Bob sends to the same CA the same public key of Alice (copied from another certificate) along with his identifier. If the CA doesn’t perform POP, it will create another certificate with the same public key associated to Bob, and here lies the problem. 

When Alice signs a document, if someone contests that document, she could claim that Bob signed it, thus negating non-repudiation. Conversely, Alice could claim she signed a document, but Bob may argue that it was him. In both cases, there is confusion about who signed the document, which compromises non-repudiation and attribution, especially in legal matters.

Therefore, **POP** is essential in ensuring non-repudiation, particularly when legal accountability is involved.


### Countermeasures

The best approach is to perform **Proof of Possession (POP)** at the moment of performing the signature. When the signature is created, it could include a reference to the certificate that associates the public key to the identity, typically by inserting the hash of the certificate together with the data. This way, the signature value becomes a function not only of the data but also of the certificate, thereby ensuring non-repudiation. Unfortunately, this method is currently unsupported in signature standards, so a custom protocol must be created.

An alternative solution is for the CA to ensure that Bob does not receive the certificate without performing POP. When the CA creates a certificate, it requests POP from the certificate requester, typically by asking for the private key as POP. The key is usually sent **out of band**, meaning the keys are created by the CA and delivered to the user via a secure token (such as the smart card used at Politecnico). The possession of the token serves as proof of possession.

Another solution is for the CA to keep a copy of all the private keys, but this raises the issue of how to protect those keys efficiently. While this method is more secure, it requires a secure device or online methods. If the key is used for both signature and encryption, **self-signed formats** like [[Advanced ISS/PKC/PKCS 10|PKCS#10]] could be used. In such cases, the request must include a signature (which uses the private key) even if no certificate is yet issued. This demonstrates possession of the private key.

For encryption keys not used for signature, a **challenge-response protocol** can be employed. The certificate is sent encrypted, and the other side must decrypt it and send it back, proving possession of the private key.
