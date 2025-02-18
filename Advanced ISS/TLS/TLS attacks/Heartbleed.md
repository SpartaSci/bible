---
tags:
  - attack
---

[Heartbleed](https://heartbleed.com/)

Setting up a TLS connection is an expensive operation (due to the handshake, negotiation, etc...). So, this extension was introduced:


**RFC6520 = TLS/DTLS heartbeat extension**

to keep a connection alive without the need to constantly renegotiate the SSL session ([[Advanced ISS/TLS/DTLS|DTLS]]!)
Even if there are no data to be transmitted, in order to avoid the system to automatically shutdown the TLS channel due to a timeout (of either the software managing TLS or the underlying TCP channel), a message is periodically sent

Also useful in PMTU (Path Maximum Transmission Unit) discovery, thanks to this extension, one could send heartbeat messages of different dimensions just to see if they get through (and they’re not discarded because they exceed the MTU);


[cve-2014-0160](https://nvd.nist.gov/vuln/detail/cve-2014-0160) = openSSL implementation bug (buffer over-read)

TLS server sends back more data (up to 64kB) than in the heartbeat request;

see http://xkcd.com/1354/

attacker can get sensitive data stored in RAM, such as user+pwd and/or server private key (if not using HSM);

an attacker could send a specially crafted heartbeat message with a fake length field, claiming to send more data than actually provided. Even though there’s no correspondence between the two sizes, the server will rely on the claimed size and it will send a portion of data, as big as the claimed size, which is adjacent in memory to the data that was supposed to be sent to reply to the message;


