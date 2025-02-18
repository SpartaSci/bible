### On-line Certificate Status Protocol

It is a client-server protocol to verify if a certificate is valid **NOW** (this is the major limitation), it cannot answer about the past.

- **Example:** If, as before, Lioy is creating the grades for an exam and there is a signature on them but does not have a CRL, and this document has to be verified in 3 years, it is needed, at the moment of the signature, to query the OCSP server and to save the OCSP answer. We do not archive the CRL but the OCSP answer, with all the problems related, because the OCSP answer is signed by the server itself. So the server needs to be trusted and to also keep the certificate of the server.

OCSP provides an answer about the validity of the certificate. The answer can be only:

- **Good**
- **Revoked** – providing also the `revocationTime` and `revocationReason` (similar to CRL)
- **Unknown** – if we are requesting information about a certificate that was never issued.

The responses are digitally signed by the server to avoid fake responses. The signature certificate of the OCSP server cannot be verified with OCSP itself. 

OCSP can be used directly (as a protocol), but most of the time, it is encapsulated within HTTP or HTTPS to get some additional security. Even if there is HTTPS, the answer is signed by the server; we do not rely on TLS to protect the transaction.
