---
tags:
  - hardware
---
![](https://www.researchgate.net/publication/313543781/figure/fig1/AS:729313057980417@1550893191686/Arbiter-PUF-architecture.ppm)


The **input challenge C** determines the PATH by controlling the multiplexers ( 0 signal from the same row, 1 from the other)

A rising signal is given to both paths simultaneously, the signals race through the two delay paths, and the arbiter (latch) at the end decides which signal is faster, generating Y = 1 or Y = 0
The output is one bit

	