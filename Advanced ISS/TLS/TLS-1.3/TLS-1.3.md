
Design targets:
- reducing handshake latency
- encrypting more of the handshake (for security and privacy)
- improving resiliency to cross-protocol attacks (e.g., downgrade attack, attacks to application layer protocols, etc...)
- removing legacy features 

RFC-8446 (August 2018)


# changes

## TLS-1.3: key exchange

- remove static RSA and DH key exchange
	- it’s not forward secrecy −→ problem with Heartbleed attack;
	- difficult to implement correctly −→ problem with the [[Advanced ISS/TLS/TLS attacks/Bleichenbacher attack (and ROBOT)|Bleichenbacher attack (and ROBOT)]];
- use DHE but do not permit arbitrary parameters
	- (2015) LogJam and weakDH trick servers to use small numbers for DH (just 512-bit);
	- (2016) Sanso finds openSSL generates DH values without the required mathematical properties;
- TLS-1.3 uses only DHE with a few predefined groups;



## TLS-1.3: message protection
previous pitfalls:
- use CBC mode and authenticate-then-encrypt
	- culprit for Lucky13, Lucky Microseconds, POODLE;
- use RC4
	- (2013) plaintext can be recovered due to measurable biases;
- use of compression
	- culprit for CRIME attack;

TLS-1.3 uses only safe cryptography:
- does not use CBC and authenticate-then-encrypt
	- **only AEAD modes are permitted**;
- dropped RC4, 3DES, Camellia, MD5, and SHA-1
	- **only modern crypto algorithms and no compression at all** (however, compression could still be applied by application layer protocols);



## TLS-1.3: digital signature
previous pitfalls:
- RSA signature of ephemeral keys
	- done wrongly with the PKCS#1v1.5 schema;
- handshake authenticated with a MAC, not a signature
	- makes possible attacks such as FREAK because of the usage of a symmetric key (much easier to brute force than an asymmetric key);

TLS-1.3 uses:
- RSA signature with the modern secure **RSA-PSS schema**;
- **the whole handshake is signed**, not just the ephemeral keys;
- modern signature schemes;

## TLS-1.3: ciphersuites
avoid the complexity of previous versions, huge list, combinatorically increasing for every new algorithm;

TLS-1.3 specifies only orthogonal elements:
- Cipher (&mode) + HKDF hash;
- no certificate type (RSA, ECDSA, or EdDSA);
	- assumed to be X.509 with support for the algorithms above;
- no key exchange (DHE/ECDHE, PSK, or PSK+DHE/ECDHE);


only 5 ciphersuites:
- TLS AES 128 GCM SHA256;
- TLS AES 256 GCM SHA384;
	- for some reason sha is not double of aes, just because
	- is not used for integrity but for generation, so we dont need 512 bits of digest
- TLS CHACHA20 POLY1305 SHA256;
	- faster, due to the usage of ChaCha20 (stream cipher);
- TLS AES 128 CCM SHA256;
- TLS AES 128 CCM 8 SHA256 (deprecated);


[[Advanced ISS/TLS/TLS-1.3/EdDSA|EdDSA]] -> [[Advanced ISS/TLS/TLS-1.3/HKDF|HKDF]]



# TLS-1.3


[[Advanced ISS/TLS/TLS-1.3/TLS 1.3 key schedule|TLS 1.3 key schedule]]

[[Advanced ISS/TLS/TLS-1.3/TLS-1.3 handshake|TLS-1.3 handshake]]

[[Advanced ISS/TLS/TLS-1.3/TLS and PKI|TLS and PKI]]

[[Advanced ISS/TLS/TLS-1.3/OCSP stapling|OCSP stapling]]
