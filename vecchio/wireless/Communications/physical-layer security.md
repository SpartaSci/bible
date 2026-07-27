---
tags:
  - wireless
  - communication
  - ISO-OSI/0
---
> Physical layer security aims at exploiting the **randomness** inherent in noisy channels to provide an additional level of protection at the physical layer. Perfect secrecy is achievable if the channel is **unknown** to unauthorized users, or the channel of the unauthorized users is more noisy than that of the authorized users

**Cryptography** permits demodulation, but the message **cannot** be understood.

**Physical Layer Security** do not allow demodulation and does not rely on the assumption of limited computational power of the attacker.

Security at physical layer is not intended to replace cryptographic security, but rather, it affords an **additional** protection layer.


# methods 

## channel approaches
- RF fingerprinting: Dynamic **fingerprinting** for intrusion detection
- [ACDM](https://telcomatraining.com/glossary/acdm-algebraic-channel-decomposition-multiplexing/) precoding: use of singular value decomposition for generating transmitted code vectors
- randomization of [MIMO](https://en.wikipedia.org/wiki/MIMO) Transmission Coefficients: achieving perfect secrecy by randomizing [MIMO](https://en.wikipedia.org/wiki/MIMO) coefficients

## code approaches
- error correction coding: advanced channel coding and **AES** cryptosystem for secure communication
- [[signal analysis/spread spectrum|spread spectrum coding]]: direct-sequence [[signal analysis/signal multiplexing#CDM - Code Division Multiplexing|CDMA]] and [[wireless/Communications/Frequency hopping|Frequency hopping]] Spread Spectrum ([FHSS](https://en.wikipedia.org/wiki/Frequency-hopping_spread_spectrum))

## power approaches
- directional antennas: improved spatial reuse and data availability using [beamforming](https://en.wikipedia.org/wiki/Beamforming)
- artificial noise scheme: generation of artificial noise to impair intruder's channel while maintaining secrecy for the legitimate receiver

## signal design approaches
- discriminatory channel estimation: use of artificial noise to **degrade** eavesdropper's **channel estimation**
- multistage training-based channel estimation: minimization of mean squared error subject to constraints using channel feedback