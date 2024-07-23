---
aliases:
  - AH
---
The AH protocol guarantees *data integrity*, *data origin authentication* (source authentication), and *anti-replay* protection. 

The AH **header** is inserted between the IP header and the payload, and it contains several fields:
- **Next Header**: 8 bits used for indicating the next protocol in the chain that is contained into the payload.
- **Payload Length**: 8 bits indicating the length of the payload.
- **Reserved**: 16 bits are reserved.
- **Security Parameter Index (SPI)**: it uses 32 bits and it contains information about the session ID and about how to verify a signature (algorithm used and reference to key).
- **Sequence Number**: 32 bits for the sequence number used to avoid replay attacks
- **Authentication Data**: 32 bits or more that contain the crypto signature


![](https://www.researchgate.net/publication/341151254/figure/fig1/AS:887753323593729@1588668294178/Authentication-Header-Format.ppm)
