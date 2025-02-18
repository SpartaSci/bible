### How to Display an X.509 Certificate

The following are some useful commands to manage certificates with **OpenSSL**:

- **`openssl asn1parse`**
  - Displays the actual ASN.1 structure in abstract syntax notation.
  - May convert from the input format (PEM or DER) to DER.

- **`openssl x509`**
  - Signs/verifies a certificate.
  - The `-text` option displays the content of the certificate in text format.

- **`dumpasn1`**
  - This tool is not part of OpenSSL but displays the content of the certificate in a similar way to `asn1parse`.

#### ASN.1 Format Storage
When managing certificates, the ASN.1 format of the certificate can be stored in two different ways:

- **DER (Distinguished Encoding Rules)**: 
  - A binary encoding of ASN.1 (a subset of BER, Basic Encoding Rules).

- **PEM**: 
  - An armored base64 encoding of DER.

### Useful Options for OpenSSL
*Note: Refer to the image on the right for some useful options for OpenSSL that are beneficial for the lab.*
