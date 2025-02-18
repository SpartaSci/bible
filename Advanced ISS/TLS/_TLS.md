---
tags:
  - confidentiality
  - authentication
  - integrity
aliases:
  - TLS
---

TLS (was SSL) was first proposed by Netscape Communications and is to achieve a secure transport channel (so at session level).


TLS is esily applicable to all protocols based in TCP: HTTP, SMTP, NNTP, FTP, TELNET...

SSL-2, SSL-3, then TLS (Transport layer Security)T LS-1.0, TLS-1.1, TLS 1.2, TLS-1.3;


> [!Danger] **everything below TLS-1.2 is insecure and deprecated**

# goal
## **Peer authentication (server, server+client)**
via asymmetric challenge response:
- implicit: the server uses its private key to sign its public key
- explicit: the client uses a key sent by the server

the **server authenticates** itself by sending its public key (X.509 Certificate) and by responding to an implicit asymmetric challenge.
the **client authentication** (with public key, X.509 certificate, and explicit challenge) is optional.

if one of the previous steps fails the channel is closed before the client can talk to the application

Especially for e-payments, peer authentication is mandatory for the server because the client needs to open a secure channel with the right server.

## Message confidentiality
**Message confidentiality** is achieved by symmetric encryption.

The client generates a session key used for symmetric encryption of data (RC4,3DES,IDEA,AES,...)

key exchange with the server occurs via public key cryptography ([[crypto/public key/RSA|RSA]], [[crypto/public key/Diffie-Hellman|Diffie-Hellman]],Fortezza-KEA)

since TLS-1.2 authenticated encryption is also available (but optional)

## Message authentication and integrity
**Message authentication and integrity** MAC calculation [[Advanced ISS/TLS/concepts/TLS - computation of MAC|TLS - computation of MAC]]

For authentication and integrity of the data exchanged over the channel the protocol uses: 
- a key digest (SHA-1 or better)
- an *implicit* MID (Message identifier) to avoid replay and cancellation

**Protection against replay and filtering attacks**
- Filtering attack: some messages are discarded by the attacker
- **Implicit record number** (used in MAC computation!) plus layering on top of TCP. Since we're using a **reliable transport protocol** like TCP, we can assume that data will arrive in the same order as it was sent.





# TLS 

[[Advanced ISS/TLS/concepts/TLS architecture|TLS architecture]] 
-> [[Advanced ISS/TLS/concepts/TLS record format|TLS record format]]
-> [[Advanced ISS/TLS/concepts/TLS handshake protocol|TLS handshake protocol]]
-> [[Advanced ISS/TLS/concepts/TLS change cipher spec protocol|TLS change cipher spec protocol]]
-> [[Advanced ISS/TLS/concepts/TLS alert protocol|TLS alert protocol]]


[[Advanced ISS/TLS/concepts/perfect forward secrecy|perfect forward secrecy]] -> [[Advanced ISS/TLS/concepts/ephemeral mechanisms|ephemeral mechanisms]]


# versions
[[Advanced ISS/TLS/versions/TLS 1.0 (SSL 3.1)|TLS 1.0 (SSL 3.1)]]

[[Advanced ISS/TLS/versions/TLS 1.1|TLS 1.1]]

[[Advanced ISS/TLS/versions/TLS 1.2|TLS 1.2]]


## TLS evolution
As part of ClientHello and ServerHello, the client and server can send the list of supported TLS extensions:

ciphersuites / encryption:
- (RFC-3268) [[crypto/symmetric/block/AES|AES]];
- (RFC-4492) ECC;
- (RFC-4132) Camellia;
- (RFC-4162) SEED;
- (RFC-6209) ARIA;

ciphersuites / authentication:
- (RFC-2712) [[Advanced ISS/TLS/kerberos|kerberos]];
- (RFC-4279) pre-shared key (secret, DH, [[crypto/public key/RSA|RSA]]);
- (RFC-5054) SRP (Secure Remote Password);
- (RFC-6091) OpenPGP;

compression:
- (RFC-3749) compression methods + Deflate;
- (RFC-3943) protocol compression using LZS;

other:
- (RFC-4366) extensions (specific and generic);
- (RFC-4681) user mapping extensions;
- (RFC-5746) renegotiation indication extensions;
- (RFC-5878) authorization extensions;
- (RFC-6176) prohibiting SSL-2;
- (RFC-4507) session resumption w/o server state;
- (RFC-4680) handshake with supplemental data;



# TLS attack
**implementation errors**:
- [[Advanced ISS/TLS/TLS attacks/Heartbleed|Heartbleed]], BERserk, goto fail;
- Lucky13 (feb-13) timing side-channel attack, it's a variant of Vaudenay's attack that works even if that one was fixed
- Lucky Microseconds (nov-2015) variant of Lucky13 to attack s2n (Google TLS library claiming to be more secure and resistant to Lucky13)

**protocol design errors**:
- (theoretical) SLOTH, CurveSwap
- (require high resources) WeakDH, LogJam, [[Advanced ISS/TLS/TLS attacks/FREAK|FREAK]], SWEET32
- (practical and dangerous) [[Advanced ISS/TLS/TLS attacks/POODLE|POODLE]], [[Advanced ISS/TLS/TLS attacks/Bleichenbacher attack (and ROBOT)|ROBOT]]


[[Advanced ISS/TLS/TLS attacks/CRIME (2012)|CRIME (2012)]]

[[Advanced ISS/TLS/TLS attacks/BREACH 2013|BREACH 2013]]

[[Advanced ISS/TLS/TLS attacks/BEAST (2011)|BEAST (2011)]]




# TLS extension, problems and solutions


[[Advanced ISS/TLS/ALPN|ALPN]]

[[Advanced ISS/TLS/TLS False Start|TLS False Start]]

[[Advanced ISS/TLS/TLS attacks/TLS downgrade problem|TLS downgrade problem]]
-> [[Advanced ISS/TLS/TLS Fallback Signaling Cipher Suite Value (SCSV)|TLS Fallback Signaling Cipher Suite Value (SCSV)]]


[[Advanced ISS/TLS/TLS session tickets|TLS session tickets]]

[[Advanced ISS/TLS/TLS and virtual servers|TLS and virtual servers]]


# TLS 1.3
[[Advanced ISS/TLS/TLS-1.3/TLS-1.3|TLS-1.3]]

