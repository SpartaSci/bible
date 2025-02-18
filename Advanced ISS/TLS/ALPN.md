---
tags:
  - extension
---
**ALPN extension (Application-Layer Protocol Negotiation)**

RFC-7301;

application protocol negotiation (for TLS-then-proto) to speed up the connection creation, avoiding additional roundtrips for application negotiation:

(**ClientHello**) ALPN=true + list of supported app. protocols;

(**ServerHello**) ALPN=true + selected app. protocol;

Without any negotiation the client would have to try to create a TLS channel over and over again trying to use (one at a time) all the application protocols that it supports until (eventually) it finds an application protocol supported both by itself and the server;

important to negotiate HTTP/2 and QUIC:
- Chrome & Firefox support HTTP/2 only over TLS;

useful also for those servers that use different certificates for the different application protocols;

some possible values: http/1.0, http/1.1, h2, h2c;