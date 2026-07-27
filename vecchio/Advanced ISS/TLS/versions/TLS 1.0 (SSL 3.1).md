
Transport Layer Security
standard IETF:
- TLS-1.0 = RFC-2246 (jan 1999);

TLS-1.0 = SSL-3.1 (99% coincident with SSL-3);

emphasis on standard (i.e. not proprietary) digest and asymmetric crypto algorithms;

mandatory cipher suite:
- DH + DSA + 3DES;
- HMAC-SHA1
	- standard HMAC (SSL 3.0 uses a custom HMAC defined by Netscape itself);
	- ...that is the cipher suite
- TLS_DHE_DSS_WITH_3DES_EDE_CBC_SHA: Diffie Hellman Ephemeral and Digital Signature Standard with triple DES in Encrypt-Decrypt-Encrypt CBC mode and SHA1;

at the time, RSA was patented. In order to implement it outside the US, a tax had to be payed. That’s why the cipher suite is using DSA (which was free) instead of RSA;