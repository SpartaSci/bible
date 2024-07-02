> OWE is defined to encrypt wireless traffic in open and public network such as coffee shops, airports..

OWE is based on [[crypto/public key/Diffie-Hellman|Diffie-Hellman]] and HMAC-based **Extract-and-Expand key Derivation function** to establish the [[wireless/WLAN - wifi/Security/802.11i#SRN - Robust Security Network Association|PMK]] that can be used for traffic encryption.

Both [[crypto/Elliptic curve|Elliptic curve]] and [[crypto/Finite Field|Finite Field]] are supported by OWE

The focal idea is to carry **ECDH public key** in the *association requests and responses* in order to generate a symmetric encryption key

