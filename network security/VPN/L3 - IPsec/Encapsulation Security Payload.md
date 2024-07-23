---
aliases:
  - ESP
---
The ESP protocol guarantees *data confidentiality* (the data and ESP trailer are encrypted, and the next header field is in the ESP trailer, which is also encrypted), *data integrity* (authentication field similar to AH), and *host authentication*header

![](https://docs.strongswan.org/docs/5.9/_images/espHeader.png)

![](https://docs.strongswan.org/docs/5.9/_images/espTransportModePacket.png)


