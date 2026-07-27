---
tags:
  - extension
---

# problem
virtual server (frequent case with web hosting)
- different logical names associated to the same IP address
- e.g. home.myweb.it=1.2.3.4, food.myweb.it=1.2.3.4


easy in HTTP/1.1: the client uses the Host header to specify the server it wants to connect to;

but difficult in HTTPS:
- because TLS is activated before HTTP;
- which certificate should be provided?
- the certificate must contain the server’s name, otherwise a name mismatch error occurs and the channel is closed;


# solution

collective (wildcard) certificate:
	- e.g. CN=\*.myweb.it (any common name which is ending with .myweb.it);
	- private key shared by all servers:
		- not so good if the servers are managed by different people that could impersonate each other;
	- different treatment by different browsers;

X.509 certificate with a list of servers in the subjectAltName field:
	- private key shared by all servers;
	- need to re-issue the certificate at any addition or cancellation of a server (rather impractical);

use the SNI (Server Name Indication) extension:
- in ClientHello (permitted by RFC-4366);
- limited support by browsers and servers;