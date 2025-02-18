

The last class contains only one extension, which is named **CRL Distribution Point (CRLDP or CDP)**. This extension indicates that inside the certificate there is a pointer to the location where it is possible to download a CRL (Certificate Revocation List) related to this specific certificate. 

This is important because if someone is performing a signature (using a private key) and sends a user the certificate (with the corresponding public key), it is possible to perform a cryptographic verification on the signature. However, an additional check must be performed: “Is this certificate (trusted and) valid or not?” 

One way to check this is to see if the certificate appears in a CRL (indicating it has been revoked). To retrieve the CRL associated with this certificate, the CRLDP extension can provide a pointer to the internet location of that CRL. When a certificate is received, if it contains the CRLDP (as this is an optional extension), it is possible to follow that pointer, download the CRL, and determine whether the certificate has been revoked or not.

There are three ways for a pointer:
- **Directory entry**: Points to a location in a directory.
- **Email**: Sends an email to request the CRL.
- **URL**: Directly downloads the CRL.

The best choice is the URL, as it allows for direct downloading of the CRL. Using an email address is riskier, as the CRL can be quite large and may not fit within an email. Therefore, using a URL is strongly suggested. This extension can be marked as critical or non-critical.
