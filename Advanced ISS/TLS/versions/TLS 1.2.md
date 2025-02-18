RFC-5246 (August 2008);

cipher suite specifies also the PRF (pseudo-random function) used to generate client/server random;

extensive use of SHA-256 (e.g. in Finished, HMAC);

support for authenticated encryption (AES in GCM or CCM mode);

incorporates the protocol extensions (RFC-4366) and the AES cipher suite (RFC-3268);

default cipher suite TLS_RSA_WITH_AES_128_CBC_SHA
- RSA now free of charge. So, it’s used instead of DHE;
- SHA: sha-256 (by default);

IDEA (algorithm used in the 1st version of PGP) and DES cipher suites deprecated;