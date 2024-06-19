> OWE is defined to encrypt wireless traffic in open and public network such as coffee shops, airports..

OWE is based on [[cybersec/enc/public key/Diffie-Hellman|Diffie-Hellman]] and HMAC-based **Extract-and-Expand key Derivation function** to establish the [[wireless/WLAN/Security/802.11i#SRN - Robust Security Network Association|PMK]] that can be used for traffic encryption.

Both [[cybersec/crypto/Elliptic curve cryptography|Elliptic curve cryptography]] and [[cybersec/crypto/Finite field cryptography|Finite field cryptography]] are supported by OWE

The focal idea is to carry **ECDH public key** in the *association requests and responses* in order to generate a symmetric encryption key

