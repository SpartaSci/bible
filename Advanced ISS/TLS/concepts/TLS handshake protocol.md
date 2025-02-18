
[[Advanced ISS/TLS/_TLS|TLS]]

# overview

1. agree on a set of algorithms for confidentiality and integrity
2. exchange ransom numbers between the client and the server to be used for the subsequent generation of the keys
3. establish a symmetric key by means of public key operations (RSA, DH)
4. negotiate the session-id
5. exchange the necessary certificates, used to ensure that the public key used by the server and the client actually belong to them


![[Advanced ISS/TLS/_image/handshake.png]]

[[#Client Hello]] -> 
<- [[#Server hello]]
<- [[#Certificate (server)]]
<- [[#Certificate request]]
<- [[#Server key exchange]]
[[#Certificate (client)]] ->
[[#Client key exchange]] ->
[[#Certificate verify]] -> 




## Client Hello
- SSL version preferred by the client (highest supported)
- 28 pseudo-random bytes (**Client Random**)
- a session-id
	- 0 to start a new session
	- different from 0 to ask to resume a previous session
		- a server may reject such request to achieve high levels of security, because the reuse of the same parameters for a long time period could give enough information to an attacker for crypto-analysis
		- resuming a session in a load balanced environment (multiple servers) is a difficult task (in such cases it's probably better to start a new session)
- list of **cipher suites** (algorithms for encryption + key exchange + integrity) supported by the client
- list of compression methods supported by the client




## Server hello
- SSL version chosen by the server
	- should be the highest version in common with the client
	- the server may close the connection due to an insufficient security level (if the client only supports SSL and not TLS). So the security level is server-based
- 28 pseudo-random bytes (**Server Random**)
- a session-id
	- new session-id either if sessione-id=0 in the client-hello or if the server has rejected the session-id proposed by the client (in order to start a new session from scratch)
	- session-id proposed by the client if the server accepts to resume the session
- **[[Advanced ISS/TLS/concepts/cipher suite|cipher suite]]** chosen by the server
	- should be the strongest one in common with the client
- compression method chosen by the server



## Certificate (server)

- Certificate for server authentication
	- the subject/subjectAltName attribute of the certificate must be equal to the identity of the server (server's DNS name, IP address, etc)
		- in the past, browsers used to be more tolerant: e.g. if you requested a certificate for www.polito.it but the server responded with a certificate for web.polito.it the browser was simply displaying a warning message “if you think this web site is secure, go ahead”. Now, if there’s a mismatch between these names, the connection is closed;
	- the whole chain of CAs (up to a trusted root) MUSt be sent along the certificate:
		- the chain MUST NOT include the [[Advanced ISS/TLS/root CA|root CA]] since that is self-signed and so it cannot be cryptographically verified
		- the client must look at the chain to check that it starts from a trusted CA (not a root CA)
		- clients with a bad implementation may accept certificates whose chains star from fake self-signed root CAs
- can be used only for signing or (in addition) also for encryption:
	- described in the field keyusage
	- if it's used only for signing, then the phase for server-key exchange (the phase to exchange the ephemeral key for encryption of the pre-master secret)) is required as well



## Certificate request

Only if the server requests client authentication (so it is optional)
Specifies also the list of CAs trusted by the server (the browsers show to the users (for a connection) only the certificates issued by trusted CAs)


## Server key exchange
It's the message that carries the public key for key exchange (ephemeral key) [[Advanced ISS/TLS/concepts/perfect forward secrecy|perfect forward secrecy]] [[Advanced ISS/TLS/concepts/ephemeral mechanisms|ephemeral mechanisms]]e

needed only in the following cases:
- the RSA server certificate is usable only for signature 
- anonymous or ephemeral DH is used to establish the pre-master secret
	- anonymous DH: ephemeral keys are not signed (faster but less secure). This is a problem if the attacker is an active one, that can manipulate the traffic (e.g. Man In The Middle DH attack). If the attacker can only read the traffic (passive attacker), this is not a problem;
	- ephemeral DH: the word “ephemeral” is used only when the parameters are signed (it’s a convention);
- there are export problems that force the use of ephemeral RSA/DH keys;
- Fortezza (secret method used only by US army);

Explicitly signed by the server. This is the *only* message explicitly signed by the server. Since it's optional, we can't always rely on it for authentication.



## Certificate (client)
it's the message that carries the certificate for the client authentication

the certificate must have been issued from one CA which is in the list of trusted CAs sent by the server with the Certificate Request message.

## Client key exchange
The client generates symmetric keys and sends them to the server in various ways:
- pre-master secret encrypted with the server RSA public key (ephemeral or from its X.509 certificate, if such certificate is usable for encryption);
- public part of DH;
- Fortezza;

if the server is the authentic one, it will succeed in decrypting whatever the client has sent by using its own private parameters;


## Certificate verify
explicit test signature done by the client;

hash computed over all the handshake messages before this one and encrypted with the client private key so that the server can verify it;

used only with client authentication (to identify and reject fake clients);


## Change cipher spec

[[Advanced ISS/TLS/concepts/TLS change cipher spec protocol|TLS change cipher spec protocol]]

triggers the change of the algorithms to be used for message protection;
– remember that the 1st message has no protection;

allows to pass from the previous unprotected messages to the protection of the next messages with the negotiated algorithms and keys;

theoretically, it’s a protocol on its own and it isn’t part of the handshake;

some analysis suggest that it could be eliminated because of the “finished” message;


## Finished
**first message protected with the negotiated algorithms;**

if we already completed the previous messages, we’re now waiting for the “finished” message and there’s no need to [[Advanced ISS/TLS/concepts/TLS change cipher spec protocol|change cipher spec]]. 
That’s why, in the latest TLS versions, the “change cipher spec” message has been removed;


**very important to authenticate the whole handshake sequence**:
- contains a MAC computed over all the previous handshake messages (but change cipher spec) using as a key the master secret;
- without the right pre-master secret (decrypted with the server’s private key) the other keys cannot be properly generated and so the final MAC computation will fail, proving that the server is not the authentic one;
- prevents rollback man-in-the-middle attacks (version downgrade or cipher suite downgrade);
	- the 1st message, used to establish the list of cipher suites, is not protected and could be changed by a MITM attack (e.g. AES changed into weaker algorithm);


different for client and server;
the “finished” message sent by the client to the server and the one sent by the server to the client are clearly different because both entities sent to each other different messages (so, they will compute two different MACs);


# example

## TLS, no ephemeral key, no client auth (base)
The server has a certificate valid for both digital signature and encryption.
1. The client sends the cipher suites list and the client random (along with other stuff);
2. The server replies with the selected cipher suite and the server random;
3. The server must be authenticated. So, it automatically sends its certificate (without the client requesting it) which, in addition to the signature (that must always be present), contains the keyEncipherment flag. So, as we said, this certificate can also be used for encrypting keys;
4. The client generates a key, i.e. the pre-master secret, and encrypts it with the server’s public key;
5. Since the client can compute the master secret from the pre-master secret and, afterwards, it can derive from it (in combination with server random and client random) the keys for MAC and encryption, it now has all the pre-requisites to enhance the security level (because it knows all the algorithms and parameters). So, it sends the “change cipher spec” message to the server;
6. The client sends the “finished” message;
7. Since now the server knows too the algorithms and the keys (because it received the pre-master secret from the client), it can activate protection on its side. So, it sends the “change cipher spec” message to the client;
8. The server sends the “finished” message to the client. If the MAC is wrong, the client closes the connection because it understands that the server is not the real one;


## TLS, no ephemeral key, client auth
The * symbol refers to a message that has been added with respect to the previous example:
1. The client sends the cipher suites list and the client random (along with other stuff);
2. The server replies with the selected cipher suite and the server random;
3. The server must be authenticated. So, it automatically sends its certificate (without the client requesting it) which, in addition to the signature (that must always be present), contains the keyEncipherment flag. So, as we said, this certificate can also be used for encrypting keys;
4. \* The server sends the “certificate request” and expects the client to send back (in step 5*) a certificate whose chain of CAs goes up to one CA which is in the list of trusted CAs sent to the client. The cert type field contains the type of the certificate requested by the server (e.g., X.509);
5. \* Client send the certificate
6. The client generates a key, i.e. the pre-master secret, and encrypts it with the server’s public key;
7. \* The signature is not performed at step 6 but it’s postponed because, by doing so, it can protect more messages. So, the signature is performed just before sending the “finished” message. Even if the “finished” message (step 9) already includes a MAC of all the previous messages, sending this signature is a surplus for security;
8. Since the client can compute the master secret from the pre-master secret and, afterwards, it can derive from it (in combination with server random and client random) the keys for MAC and encryption, it now has all the pre-requisites to enhance the security level (because it knows all the algorithms and parameters). So, it sends the “change cipher spec” message to the server;
9. The client sends the “finished” message;
10. Since now the server knows too the algorithms and the keys (because it received the pre-master secret from the client), it can activate protection on its side. So, it sends the “change cipher spec” message to the client;
11. The server sends the “finished” message to the client. If the MAC is wrong, the client closes the connection because it understands that the server is not the real one;




## TLS, ephemeral key, no client auth
Perfect forward secrecy is guaranteed.


1. The client sends the cipher suites list and the client random (along with other stuff);
2. The server replies with the selected cipher suite and the server random;
3. This time the certificate is only valid for digital signature, so we’re forced to use an ephemeral key;
4. The server generates an asymmetric key pair on-the-fly and sends the “key exchange” message to the client which contains either an RSA key or a DH exponent signed with its long-term private key;
5. After this step, both client and server have the pre-master secret (because they’ve exchanged all necessary parameters, i.e., the keys in case they chose RSA and the exponents in case they chose DH);
6. Since the client can compute the master secret from the pre-master secret and, afterwards, it can derive from it (in combination with server random and client random) the keys for MAC and encryption, it now has all the pre-requisites to enhance the security level (because it knows all the algorithms and parameters). So, it sends the “change cipher spec” message to the server;
7. The client sends the “finished” message;
8. Since now the server knows too the algorithms and the keys (because it received the pre-master secret from the client), it can activate protection on its side. So, it sends the “change cipher spec” message to the client;
9. The server sends the “finished” message to the client. If the MAC is wrong, the client closes the connection because it understands that the server is not the real one;


## TLS, resumed session
Session resumption occurs (if permitted by the server) when opening a new connection within the same session. That means both client and server have already negotiated the algorithms, the pre-master secret and the master secret. These are the messages being exchanged:
1. The client sends the “client hello” message with a session-id $X\neq0$;
2. The server, in order to accept the session resumption, must reply by sending the “server hello” message with the same session-id X received by the client. This means that there must be a server-side database which stores, for each session-id, the corresponding negotiated algorithms and parameters. Keeping track of the session-id and the negotiated parameters for each session is a big overhead for the server. So, normally, a session-id is usable only for a limited amount of time;
3. The client sends the “change cipher spec” message to activate protection on its behalf, since it’s now able to create the new keys for this connection. Remember that, for each connection within the same session, the master secret (common to all connections within that same session) is combined with client random and server random. So, the client is able to autonomously generate the new keys;
4. The client sends the “finished” message. A (malicious) fake client won’t know how to communicate with the server. Specifically, the fake client won’t know the algorithms nor the master secret but only client random and server random (which are useless without the master secret). So, it will use the wrong key and algorithm for MAC computation. The MAC will be wrong and the server will understand that the client is an impostor. This holds also in case of a fake server, since the impostor won’t have the database with the session-id and the corresponding algorithms and keys. So, it will compute the wrong MAC and the client will shut the connection. As we can see, in session resumption, even if there’s no explicit authentication, there’s an implicit authentication mechanism thanks to the “finished” message;
5. The server sends the “change cipher spec” message and activates protection on its behalf by using the master secret in combination with client random and server random;
6. The server sends the “finished” message;


# TLS, data exchange and link teardown


After the handshake’s been successful and client and server have exchanged data, how do they close the secure channel?

Before going over that procedure, a few notes regarding data exchange:
- encryption is optional but MAC is compulsory;
- the ([[Advanced ISS/TLS/concepts/TLS - computation of MAC|implicit]]) sequence number N of the client could be different from the (implicit) sequence number M of the server, depending from whether, until that moment, they’ve exchanged the same amount of messages or not;

Client and server close the secure channel by using the TLS alert protocol:
1. The client sends the “*LAST-1. alert close notify*” message, which is protected by a MAC;
	- the MAC is needed because someone could send fake messages to force the channel closure and cause DoS;
2. The server replies with the “*LAST. alert close notify*” message. Such message is needed because of the following attack:
	- a MITM, who has control over a router between client and server, could block the communication between them. How could the server understand that communication’s been interrupted by an attack and not because the client voluntarily closed the channel?


So, the protocol needs an explicit message (LAST-1) with a corresponding acknowledgement (LAST) in order to close the channel. After sending the LAST-1 message, the client will close the channel only if it’ll receive the LAST message from the server;

In case of:
- shutdown: the OS will tell all the processes to close any remaining TLS channel;
- power failure: the other entity will know that the channel’s been closed due to an error (the power failure itself);


# TLS setup time


first TCP handshake;
then TLS handshake;
various messages can fit in a single TCP segment to reduce the round trip time (RTT);

typically this requires 1-RTT for TCP and 2-RTT for TLS:
- (C→S) SYN
	- (S→C) SYN-ACK;
- (C→S) ACK + ClientHello
	- (S→C) ServerHello + Certificate;
- (C→S) ClientKeyExchange + ChangeCipherSpec + Finished
	- (S→C) ChangeCipherSpec + Finished;

after 180 ms client and server are ready to send protected data (assuming 30 ms delay one-way);

as we can see, the client ends the TCP handshake by sending the  ACK to the server but, in order to reduce the RTT, it puts in the same segment also ClientHello. Same reasoning is adopted by the server, which replies by putting in the same segment both ServerHello and Certificate. The same happens for the other communications;