# SSH: DH key agreement (and server authN)
1. [ C ] generates a random number x, computes $e = g^x \mod p$;
2. [ C → S ] e;
3. [ S ] generates a random number y, computes $f = g^y \mod p$;
4. [ S ] computes
-  $K = e^y \mod p = g^{xy} \mod p$
-  the exchange hash: $$H = HASH(c\_version\_string|s\_version\_string|c\_kex\_init\_msg|s\_kex\_init\_msg|s\_host\_PK|e|f|K)$$
	- it’s not simply a hash but its’a a keyed digest (because it’s computed over K too);
5. [ S ] generates a signature sigH on H using the private key s host SK (may involve additional hash computation on H, e.g., RSA signature requires to compute the hash of the data to be signed);
6. [S → C] s_host_PK | f | sigH;
7. [ C ] verifies that s host PK is really the server’s public key;
	- this is a critical step, since there’s no X.509 certificate;
8. [ C ] computes K = f x mod p = g xy mod p and H = HASH(...);
- the client can now compute H too because it has computed K and it has received s host PK and f from the server. All the other parameters were already been exchanged with the server;
- K is the shared symmetric key;
9. [ C ] verifies the signature sigH on H;
- this step is authenticating the server by demonstrating that it has used the private key corresponding to the public key s host PK;
10. [C, S] H becomes the session-id;





# SSH: key derivation
Starting from K we derive 6 parameters:
- initial IV:
	- client to server = HASH( K || H || “A” || session id );
	- server to client = HASH( K || H || “B” || session id );
- encryption key:
	- client to server = HASH( K || H || “C” || session id );
	- server to client = HASH( K || H || “D” || session id );
- integrity key:
	- client to server = HASH( K || H || “E” || session id );
	- server to client = HASH( K || H || “F” || session id );
- note: session id is the H value computed for the first key exchange, and remains such even when key re-exchange is performed;



## SSH: encryption
- encryption algorithm negotiated during the key exchange;
- encryption algorithm can be different (!) in each direction;
- supported algorithms (basic set):
	- (required) 3des-cbc (w/ three keys, i.e. 168 bit key);
	- (recommended) blowfish-cbc, twofish128-cbc, aes128-cbc;
	- (optional) twofish256-cbc, twofish192-cbc, aes256-cbc, aes192-cbc, serpent256-cbc, serpent192-cbc, serpent128-cbc, arcfour, idea-cbc, cast128-cbc;
- key and IV established during the key exchange;
- all packets sent in one direction is a single data stream;
- IV is passed from the end of one packet to the beginning of the next one;
	- not a good idea because of the BEAST attack;




## SSH: MAC
- MAC algorithm and key negotiated during the key exchange;
- MAC algorithms used in each direction can be different;
- supported algorithms (basic set):
	- hmac-sha1 (required) [key length = 160-bit];
	- hmac-sha1-96 (recomm) [ key length = 160-bit];
	- hmac-md5 (opt) [key length = 128-bit];
	- hmac-md5-96 (opt) [key length = 128-bit];
- MAC = mac( key, seq number | cleartext packet )
	- sequence number is implicit, not sent with the packet;
	- sequence number is represented on 4 bytes;
	- seq number initially 0 and incremented after each packet;
	- seq number never reset (even if keys/algos are renegotiated);





## SSH: peer authentication - server
Server authentication:
- asymmetric challenge-response (explicit server signature of the key exchange hash H);
- client locally stores the public keys of the servers (danger!)
- typically in ∼/.ssh/known hosts;
- if key absent (not in known hosts yet), then it’s offered at first connection
- TOFU (Trust On First Use) danger!
- keys of trusted servers could be distributed OOB but this is risky, since it relies on human actions
and it’s not an automatic process (e.g., the security manager of a company distributes the keys
of trusted servers but each employee must manually install them on his computer);
- good practice:
- protect known hosts for authentication and integrity
- an attacker could change the content of the file;
- periodic audit/review of known hosts to quickly detect added/deleted hosts or changed keys
- must have a way to connect to all computers of a company and check the content of the
known hosts file;



## SSH: peer authentication - client
Client authentication (part of the UAP, i.e., User Authentication Protocol):
- username and password
	- exchanged only after the protected channel is created;
	- protected from sniffing but still open to other attacks (e.g. on-line password enumeration);
- asymmetric challenge-response
	- server locally stores the public keys of the users allowed to connect as a local user
		- typically in ∼local user/.ssh/authorized keys;
		- this provides both authentication and authorization (e.g., Lioy connects to Atzeni’s machine and, since his public key is stored by the server, he can now access that machine as “Atzeni”);
- good practice:
	- protect authorized keys for authentication and integrity;
	- periodic audit/review of authorized keys to quickly detect added/deleted users or changed keys;


