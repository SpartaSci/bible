### There are some types of models:

- **CA Responder (operated by the CA)**:  
  The CA signs the response with its own private key, which is quite risky because the private key of the CA must be online, so it is rarely adopted. It is possible to mitigate this problem by using a key dedicated only to OCSP signing (remember `ExtendedKeyUsage`).  
  Even if the OCSP responder is operated by the CA, it can use different keys: one for creating certificates and one to sign them. This aligns with the concept of "Authority Key Identifier" because a CA could have 3 keys: one for signing certificates, one for signing CRLs, and one for the OCSP responder. These are different functions, potentially run on different machines. This last method is the most used one.

- **Trusted responder**:  
  The OCSP server signs the responses with a pair key:cert independent of the CA for which it is responding. The company responder works in a similar way. It can also be a trusted third party (TTP) paid by the user.

- **Delegated responder (Designed or Authorized)**:  
  The OCSP server signs the responses with a pair key:cert which is different based on the CA for which it is responding. It’s a TTP paid by the CA for whom it is responding. An external server is delegated to provide the answer on the CA's behalf by providing a pair key:cert where the certificate contains `OSCP responder` as an extended key usage. This indicates that the responder is delegated by the CA to provide OSCP answers. There could be one responder that answers for multiple CAs.

As we have seen, OSCP is faster, but for real-time transactions, they are quite similar. For delayed verifications, we have problems because we need to store the information at the time of the signature.
