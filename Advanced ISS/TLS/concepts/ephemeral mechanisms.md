A technique used to implement [[Advanced ISS/TLS/concepts/perfect forward secrecy|perfect forward secrecy]]

[[Advanced ISS/TLS/TLS-1.3/TLS-1.3|TLS-1.3]] uses only ephemeral mechanism


Distinction between the following phases:
- asymmetric challenge-response, with an asymmetric key pair
- [[Advanced ISS/TLS/concepts/TLS architecture|pre-master secret]] exchange, with a **different** asymmetric key pair


That means the server's (long term) private key is used for signature generation only. So, the [[Advanced ISS/TLS/X.509 certificate|X.509]] server's certificate will have the *digital signature* flag but not the encryption one.

How can the client send the pre-master secret to the server?

The server generates a *one-time asymmetric key pair on-the-fly* (when creating a session):
- used only for the current session (after the sessions has been established, both client and server will already know the pre-master secret and the master secret)
- for authenticity, the public key must be signed with the server's long-term private key. By doing so, the server acts as a CA.
	- the public key can’t have an associated X.509 certificate because the key pair has been generated on-the-fly and the CA process is slow and often not on-line;
- DH suitable, RSA slow:
	- compromise for RSA = re-use N times;

So, we can obtain **perfect forward secrecy** because: 
- if the short-lived private key is compromised then the attacker can decrypt only the related traffic
- compromise of the long-term private key
	- is an issue for authentication, because that key is used for signing
	- is not an issue for confidentiality, because the pre-master secret can only be decrypted with the short lived private key

Example: ecdhe

