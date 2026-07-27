(Factoring RSA Export Keys) 2015
- downgrade to export-level RSA keys (512-bit), then factorization and channel decryption;
- or downgrade to export-level symmetric key (40-bit), then brute-force to crack the key;

**Freak attack (downgrade symmetric key)**
This attack is performed by an active MITM:
1. The client sends the “client hello” message with the client random, the list of supported ciphers and the list of supported curves (for elliptic curves criptography);
2. The MITM modifies the list of supported ciphers by leaving the export cipher as the only supported cipher;
3. If the server is configured to still support the export cipher, it will agree to use it and it will reply with a “server hello” message that contains the export cipher;
4. The client, even if it supports stronger algorithms, thinks that the server only supports the export cipher and so it generates a weak shared key (pre-master secret) of 40 bit only;
5. At the end of the handshake, the client sends the “finished” message, i.e., the HMAC of all previous messages computed with the weak shared key;
6. The MITM must be really fast to brute force the key in order to modify the “finished” message sent by the client, because such message contains the whole list of supported ciphers but the server received a list with only the export cipher! If the MITM succeeds in recomputing the HMAC with the modified “client hello” message (with just the export cipher), there won’t be a mismatch between the HMAC computed by the server and the (modified) HMAC sent by the client;
	- The weak key brute force consists in trying all $2^{40}$ possible pre-master secrets. Each “tested” pre- master secret is used to compute the corresponding master secret (because the attacker is assumed to know client and server randoms) which is then used to derive the key for MAC computation. If the computed MAC is equal to the MAC sent by the client to the server, it means the attacker has found the pre-master secret (weak key) and, consequentially, the master secret and the derived keys, including the MAC key which can be used to recompute (modify) the MAC;
7. The server generates a new weak shared key and sends the “finished” message related to all the previously sent messages. Since the MITM has never modified any message sent from the server to the client, the HMAC computed by the client on the messages received from the server will simply match the HMAC sent by the server in the “finished” message;
8. From now on, all traffic is encrypted with the weak shared keys and the MITM can read or modify all messages between client and server;