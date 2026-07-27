# concept
Stapling means “to put something together like paper sheets”.

CRL and OCSP automatic download is often disabled;

pushed CRL contains only some revoked certificates (e.g., compromised intermediate CAs);

browser behaviour is greatly variable in this area;
solution: OCSP stapling;
- i.e. have the server send the OCSP answer along with its certificate;
- provides privacy protection for the client because it’s the server the one who queries the OCSP responder (so, the OCSP responder doesn’t know which client is visiting the web site hosted on that server but only knows that “someone” is connecting to that server);


# implementation
OCSP Stapling is a TLS extension (to be specified in the TLS handshake);
- v1 in RFC-6066 (extension “status_request”), v2 in RFC 6961 (extension “status_request_v2”)
- with value CertificateStatusRequest (CRS);


**how it works**: the TLS server pre-fetches the OCSP responses and provides them to the client in the handshake, as part of the server’s certificate message (the OCSP responses are “stapled” to the certificate);

**benefits**:
- eliminates client privacy concern;
- the client doesn’t create a new connection to the OCSP server;
	- avoided time loss for creating such connection (speed increase);

**downside**: freshness of the OCSP responses;
- maybe the server’s caching OCSP responses for minutes or even days (it depends from the server):
- this time is a window of exposure. If the certificate gets compromised during this window, it’s possible to perform attacks;
- an attacker must be able to compromise and use the private key of the server before the server makes a new request to the OCSP server in order to succeed. Since the attacker doesn’t know how long will the OCSP (cached) response be valid, he must be really fast. As soon as he sniffs a request from the TLS server to the OCSP server (assuming that such request is an OCSP request, which is probable) he must start the attack;



TLS client MAY send (if it supports the right extension) the CSR to the server, as part of the ClientHello message, to request the transfer of OCSP responses in the TLS handshake;

the TLS server that receives a ClientHello status_request_v2 MAY return (if it supports that extension) OCSP responses for its certificate chain. OCSP responses are provided within a new message, CertificateStatus;

problems:
- servers MAY ignore the status request;
- clients MAY decide to continue anyway the handshake even if OCSP responses are not provided;

solution: **OCSP Must Staple**;


# OCSP Must Staple

X.509 certificates for servers MAY include a certificate extension
- named “TLSFeatures” (OID 1.3.6.1.5.5.7.1.24);
- defined in RFC-7633;

notation: X.509+ (certificate with the extension);

the extension informs the client that it MUST receive a valid OCSP response as part of the TLS handshake...otherwise, it SHOULD reject the server certificate;

benefits:
- efficiency: the client does not need to query the OCSP responder;
- attack resistance as it prevents blocking OCSP responses (for a specific client) or DoS attack against OCSP responder;
	- if OCSP response is not sent by the server, the client won’t connect. If the client doesn’t support the OCSP Must Staple extension, the attacks will still be successfull;



## actors and duties


**CA must**: include the extension into server certificates, if requested by the server’s owner;


**OCSP Responder must**: be available 365x24 (24h a day for the whole year) and return valid OCSP responses;


**TLS client must**:
- send the CSR extension in the TLS ClientHello message;
- understand the OCSP Must-Staple extension (if present in the server’s certificate);
- reject the server’s certificate without OCSP stapled response;

**TLS server must**:
- support OCSP Stapling by prefetching and caching OCSP response;
- provide an OCSP response in the TLS handshake;
- handle errors in communication with OCSP responders;


**TLS server administrators should**:
- configure their servers to use OCSP Stapling;
- request a server certificate with OCSP Must Staple extension;

**open issue (and potential pitfall)**: duration of OCSP stapled response caching;
- e.g., 7 days for Cloudflare...an attacker, who has compromised the server’s private key, has 7 days to exploit it!



The TLSFeatures certificate extension (for OCSP Must Stapling) prevents the following attack:
- Server S sends to the client C, along with X.509+ certificate, the OCSP response;
- An attacker compromises the private key:
	- the attacker sets up a (fake) server S’, forces C to connect to S’ (e.g., with DNS cache poisoning) and sends to C an X.509+ certificate signed with the compromised key;
		- the attacker doesn’t send any OCSP response since that would tell the client that the private key of S has been compromised;
		- OCSP responses cannot be faked because they’re digitally signed by the OCSP server (unless the attacker compromises the OCSP server’s private key too...);
- However...the attack can still be successfull if the client doesn’t support OCSP Must Staple, since it will ignore the X.509 extension (because it’s unable to understand it);



# TLS status
- F5 telemetry report (October 2021) for the top 1M servers;
- 63% have TLS-1.3 (from 80% USA to 15% China and Israel);
- 25% certs use ECDSA and 99% choose non-RSA handshake;
- 52% permit RSA, 2.5% expired certs, 2% permit SSL-3;
- encryption is abused: 83% of phishing sites use valid TLS and 80% of sites are hosted by 3.8% hosting providers;
- SSLstrip attacks still successful, so urgent need for HSTS or to completely disable plain HTTP;
- cert revocation checking mostly broken, which pushes for very short lived certs;
- by TLS fingerprinting, 531 servers potentially match the identity of Trickbot malware servers, and 1164 match Dridex servers;