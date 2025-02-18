A **Root CA (Certificate Authority)** is the top-level Certificate Authority in a public key infrastructure (PKI) hierarchy. It is responsible for issuing and managing digital certificates used to verify the identity of entities (such as websites, servers, or individuals) in a secure manner.

### Key Points about a Root CA:

1. **Trust Anchor**: The Root CA is the ultimate trust anchor in the PKI. Its public key is widely trusted by applications, browsers, and operating systems. When a digital certificate is verified, the chain of trust often ends at the Root CA.
    
2. **Self-Signed Certificate**: The Root CA has a self-signed certificate, meaning it signs its own public key to create the certificate. This certificate is typically pre-installed in trusted stores (like in browsers and operating systems).
    
3. **Intermediate CAs**: To enhance security, Root CAs usually delegate the task of issuing certificates to intermediate CAs. The Root CA signs the intermediate CA's certificate, and then the intermediate CA can issue end-entity certificates (like for websites).
    
4. **Strict Security**: Root CAs are highly protected because if their private key is compromised, it undermines the entire trust system. They operate under stringent security practices, often involving hardware security modules (HSMs) to protect their private keys.
    
5. **Examples of Root CAs**: Organizations like **DigiCert**, **VeriSign**, and **Let's Encrypt** maintain Root CAs whose certificates are trusted by major platforms. For instance, browsers like Chrome and Firefox come with a list of trusted root certificates.
    

### Trust Chain Example:

When you visit a secure website:

- Your browser checks the website's SSL/TLS certificate.
- That certificate is typically issued by an intermediate CA.
- The intermediate CA's certificate is validated by a Root CA, which is already trusted by your browser.

This process ensures a secure, trusted connection (HTTPS).