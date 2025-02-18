Edwards-curve Digital Signature Algorithm

DSA requires a [[hardware/random number generator/PRNG - Pseudo Random Number Generator|PRNG]] that can leak the private key if the underlying algorithm is broken or made predictable;

**EdDSA does not need a PRNG**

EdDSA picks a nonce based on a hash of the private key and the message, which means after the private key is generated there’s no more need for random number generators;

N-bit private and public keys, 2N-bit signatures, higher memory usage, since RSA signature is N-bit long;

Ed25519 uses **SHA-512** (SHA-2) and **Curve25519**. 
256-bit key, 512-bit signature, 128-bit security.
Balanced crypto system in combination with AES-128;


Ed448 uses SHAKE256 (SHA-3) and Curve448
456-bit key, 912-bit signature, 224-bit security;
it’s not exactly 256 bits of security but can still be assumed to form a balanced crypto system in combination with AES-256;


Curve25519 is the most widely used
- elliptic curve on the field $2^{255}$ – 19
- used also in X25519 (ECDH)

EdDSA has two standards, slightly different:
- RFC-8032 for general Internet applications, implementation details left to developers
- FIPS 186-5 specifies stringent guidelines for secure key management, generation, and implementation practices


# other improvements

all handshake messages after the ServerHello are now encrypted;

the newly introduced EncryptedExtensions message allows various extensions previously sent in the clear in the ServerHello to also enjoy confidentiality protection;


the key derivation functions have been redesigned (to allow easier analysis by cryptographers thanks to their key separation properties) and [[Advanced ISS/TLS/TLS-1.3/HKDF|HKDF]] is used as an underlying primitive;


the handshake state machine has been significantly restructured to be more consistent and to remove
superfluous messages such as ChangeCipherSpec (except when needed for middlebox compatibility);
- middlebox: reverse-proxy (server side) and forward-proxy (client side), i.e., firewalls to check, respectively, incoming and outgoing traffic. Some middle boxes may still require the ChangeCipherSpec message;