*Curly braces mean that the message is encrypted* 

**Key share**: since, in TLS-1.3, we always use ephemeral keys, we always need to share our public DH/ECDH

after the server sends the “key share” message, the client and server are able to create the pre- master secret and to derive all necessary keys from it. That’s why all following messages are encrypted;

![](https://cf-assets.www.cloudflare.com/slt3lc6tev37/1hr3R0qLxh2XIklK8lNJdh/6447dd2d0e1530315d8fa8509a533aca/TLS-1.3.007.png)



**TLS-1.3 handshake: notes**


**client request**
ClientHello with client random, supported protocol versions, supported ciphersuites;

contains extensions for key exchange:
- key share = client (EC)DHE share;
- signature algorithms = list of supported algorithms;
- psk key exchange modes = list of supported modes (to exchange pre-shared keys);
- pre shared key = list of PSKs offered;

**server response**
ServerHello (server random, selected version, cipher suite);

key exchange
- key share = server (EC)DHE share;
- pre shared key = selected PSK;

server parameters
- { EncryptedExtensions } = responses to non-crypto client ext;
- { CertificateRequest } = request for client certificate (optional);

server authentication
- { Certificate } = X.509 certificate (or raw key, RFC-7250);
- { CertificateVerify } = signature over the entire handshake;
- { Finished } = MAC over the entire handshake;

[ Application Data ];
- encrypted with transport key and no more with the handshake key;


**client finish**
client authentication
- { Certificate } = X.509 certificate (or raw key, RFC-7250, which is useful for small devices like IoT devices which don’t have the necessary capabilities to process X.509 certificates);
	- encrypted with the handshake key (additional layer of security since the certificate was already being digitally signed);
- { CertificateVerify } = signature over the entire handshake;
- { Finished } = MAC over the entire handshake;

[ Application Data ];
- at this point the client could already send, in the same TCP segment, application data encrypted with the new transport key that has been negotiated;




**TLS-1.3 / Pre-Shared Keys**
In TLS-1.2, in order to resume a session with DHE, you must repeat the handshake so that the ephemeral key is digitally signed by the server.

In TLS-1.3, the handshake can be safely skipped when resuming a session, because a pre-shared key is used for authentication.

PSK replaces session-id and session ticket
- one or more PSKs agreed in a full handshake and re-used for other connections;
- the keys are associated to the session (it’s not anymore a matter of resuming “session n. 35” but now we want to “continue using PSK n. 35”);

PSK and (EC)DHE can be used together for [[Advanced ISS/TLS/concepts/perfect forward secrecy|perfect forward secrecy]](IMPORTANT)
- resuming a session would go against perfect forward secrecy because it would skip the ephemeral key signature:
	- so, since resuming a session means to reuse the same PSK, we now use such key for authentication, rather than for signature computation and we run (EC)DHE for key agreement. The generated key pair is part of the computation of the MAC of the handshake (computed by using the previously agreed PSK). By doing so, no signature is computed (so the whole process is faster, since we don’t use asymmetric crypto) and we have perfect forward secrecy!
	- In TLS-1.2, in order to have perfect forward secrecy, we must repeat every time (EC)DHE with the signature;

PSK could also be OOB, i.e., Out Of Band (e.g. generated from a passphrase)
- this is risky if you have insufficient randomness (see RFC-4086) so that a brute-force attack could be possible;
- in general OOB PSK is discouraged;


**TLS-1.3 / 0-RTT connections**
- when using a PSK, client can send “early data” along with its first message (client request);
- early data protected with a specific key (client_early_traffic_secret)
	- does not provide forward secrecy (because it depends only upon the PSK);
	- possible some kind of replay attack (partial mitigations are feasible but complex, especially in multi-instance servers);

**TLS-1.3 / Incorrect share**
- client can send a list of (EC)DHE groups not supported by the server;
	- remember that, for DH you can’t arbitrarily choose the mathematical groups (in TLS-1.3). However, the client could still send a message with unsupported groups. That’s why we need the HelloRetryRequest message;
- server will respond with HelloRetryRequest and the client must restart the handshake with other groups;
- if also the new groups are unacceptable for the server, then the handshake will be aborted with an appropriate alert;