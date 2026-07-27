---
tags:
  - extension
---

RFC-7918;

the client can send application data together with the [[Advanced ISS/TLS/concepts/TLS handshake protocol|ChangeCipherSpec]] and Finished messages, in a single segment, without waiting for the corresponding server messages; this reduces latency to 1-RTT;

It should work without changes but there are caveats:
- Chrome and FX require [[Advanced ISS/TLS/ALPN|ALPN]] + forward [[Advanced ISS/TLS/concepts/perfect forward secrecy|secrecy]];
- Safari requires forward secrecy;

to enable TLS False Start for all browsers the server should:
- advertise supported protocols (via ALPN, e.g. “h2, http/1.1”);
- be configured to prefer cipher suites with forward secrecy;