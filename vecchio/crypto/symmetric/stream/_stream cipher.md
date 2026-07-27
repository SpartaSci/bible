---
tags:
  - confidentiality
  - symmetric
  - stream
  - encryption
---
> is a symmetric key cipher where each plaintext bit is encrypted one at time with a corresponding bit from the keysteam

**keystream** comes from a pseudo-random generator with a pseudo random seed fixed





> a stream ciphers encrypts bits individually

enc: $y_i = e(x_i) \equiv x_i + s_i \mod 2$
dec: $x_i = d(y_i) \equiv y_i + s_i \mod 2$
$d(y_i) \equiv y_i + s_i \mod 2$
$d(y_i) \equiv (x_i+s_i) + s_i \mod 2$
$d(y_i) \equiv x_i + 2s_i \mod 2$
$d(y_i) \equiv x_i\mod 2$

**mod 2 addition (and subtraction) is the same of XOR operation**

to generates the keystream we need a [[crypto/random numbers|random numbers generators]]
