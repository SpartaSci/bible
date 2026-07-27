---
aliases:
  - PFS
---



> [!Danger] Problem


[[Advanced ISS/TLS/X.509 certificate|X.509 certificates]] have some flags that specify the legal purpose of each certificate

if a server has a certificate valid for both signature and encryption then, such certificate can be used both for 
- authentication (via a signature) 
	- during the asymmetric challenge-response, the server uses its private key to perform a signature in order to prove that it is actually possesses the private key associated to the public key specified in the X.509 certificate sent to the client)
- key exchange (asymmetric encryption for the session key)
	- after the server is authenticated, the client generates the **pre-master secret**, encrypts it with the server's public key and transmits it to the server itself


but if an attacker copies all the encrypted traffic and later discovers the long-term private key by attacking the server public key, then he can decrypt all the traffic, past present and future.

That's possible because all the traffic has been encrypted with the keys derived from the master secret which can be computed by the attacker, assuming that he has stored also client and server randoms, after decrypting the pre-master secret with the server's private key.



> [!success] Solution

**Perfect forward secrecy**
it's a kind of protection for the use of asymmetric key pairs in which the compromise of a private key compromises only the current (and eventually future) traffic but not the past one

it's optional in [[Advanced ISS/TLS/_TLS|TLS-1.2]] but compulsory in [[Advanced ISS/TLS/TLS-1.3/TLS-1.3|TLS-1.3]]

can be implemented by means of proper techniques -> [[Advanced ISS/TLS/concepts/ephemeral mechanisms|ephemeral mechanisms]]
