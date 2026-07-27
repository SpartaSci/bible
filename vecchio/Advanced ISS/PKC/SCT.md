### SCT via X.509v3 Extension

The process for obtaining and utilizing a Signed Certificate Timestamp (SCT) involves several steps:

1. **CA Contacts Log Servers**: 
   - Before issuing a certificate, the Certificate Authority (CA) contacts log servers and sends a **pre-certificate** to them.

2. **Log Server Acceptance**:
   - The log server accepts the pre-certificate and logs it, confirming that the CA has promised to issue a certificate for a web server. 

3. **SCT Generation**:
   - The log server then returns the SCT to the CA, signifying that the pre-certificate has been logged.

4. **Attaching SCT to Pre-Certificate**:
   - Once the SCT is received, the CA attaches the SCT as an **X.509v3 extension** to the pre-certificate.

5. **Signing and Sending to Web Server**:
   - The CA then signs the pre-certificate (now with the SCT) and sends it to the web server.

6. **TLS Handshake**:
   - During the TLS handshake, the web server sends its certificate along with the SCT to the client (e.g., a web browser). This means the browser does not need to separately look for the SCT, as it is provided directly with the certificate.


### SCT via TLS Extension

In this scenario, the process for obtaining and utilizing a Signed Certificate Timestamp (SCT) involves the following steps:

1. **CA Issues Normal Certificate**: 
   - The Certificate Authority (CA) issues a standard certificate to the server.

2. **Submission to Log Server**:
   - The server operator (the owner of the website) submits this certificate to the log server.

3. **Log Server Sends SCT**:
   - The log server processes the submission and sends the SCT directly to the server operator.

4. **Delivering SCT to Client**:
   - The web server can now deliver the SCT to the client separately during the TLS handshake using the **`signed_certificate_timestamp`** TLS extension.

5. **Inclusion During TLS Handshake**:
   - The SCT is sent alongside the server's certificate during the TLS handshake, ensuring the client receives both the certificate and the associated SCT.


### SCT via OCSP Stapling

In this approach, the process for obtaining and utilizing a Signed Certificate Timestamp (SCT) is as follows:

1. **CA Informs Log Server**:
   - The Certificate Authority (CA) notifies the log server about the creation of the certificate.

2. **Log Response**:
   - The log server provides a response regarding the SCT, but this timestamp is not included in the certificate itself since it has already been issued to the web server.

3. **Performing OCSP Stapling**:
   - When the website performs OCSP (Online Certificate Status Protocol) stapling, it requests an OCSP response from the CA.

4. **Including SCT in OCSP Response**:
   - The OCSP response from the CA will now also contain the SCT.

5. **Transmitting SCT to the Browser**:
   - The SCT is transmitted to the browser as part of the OCSP response during the TLS handshake.

### Choosing a Strategy
Different strategies exist depending on the specific situation. For instance, if the CA provides the OCSP service, there may be no need to use the TLS approach.
