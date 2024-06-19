---
tags:
  - asymmetric
aliases:
  - public key
---
> there are two keys, if one is used for encryption (public key), the second must be use to decrypt (secret key)



Public keys are not confidential, but they must be authentic, while private one must be confidential.


> [!Success] The security is based on hard problems
> **Factoring Problem**: given a positive integer n, find its prime factor
> **Discrete Logarithm Problem**: given a prime p, a generator g and an element y find x such that $g^x \mod p = y$
> **Diffie-Hellmab problem**: given a prime p, a generator g and x,y find $g^{xy}\mod p$


[[cybersec/enc/public key/RSA|RSA]]

[[cybersec/enc/public key/Diffie-Hellman|Diffie-Hellman]]


