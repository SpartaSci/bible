![[Advanced ISS/_images/SSH_TLP.png]]


# TLP: connection and version exchange


TCP connection setup
- the sever listens on port 22 by default
- the client initiates the connection

SSH version string exchange
- both sides must send a version string of the following form:
	- SSH-ProtocolVersion-SoftwareVersion SP comments CR LF
	- where




# SSH TLP: key exchange

algorithm negotiation:
- SSH MSG KEXINIT;
- cookie (16 random bytes);
- kex algorithms;
- server host key algorithms;
- encryption algorithms client to server, ... server to client;
- mac algorithms client to server, ... server to client;
- compression algorithms client to server, ... server to client;
- languages client to server, ... server to client;
- first kex packet follows (flag);
	- attempt to guess agreed kex algorithm;


# SSH TLP: algorithm specification
- kex algorithms (note: contains HASH)
	- e.g. diffie-hellman-group1-sha1, ecdh-sha2-OID of curve;
- server host key algorithms (this is the key for server authentication)
	- e.g. ssh-rsa;
- encryption algorithms X to Y
	- e.g. aes-128-cbc, aes-256-ctr, aead aes 128 gcm;
- mac algorithms X to Y
	- e.g. hmac-sha1, hmac-sha2-256, aead aes 128 gcm;
- compression algorithms X to Y
	- e.g. none, zlib;
- complete list maintained by IANA: 
	- https://www.iana.org/assignments/ssh-parameters/ssh-parameters.xhtml

