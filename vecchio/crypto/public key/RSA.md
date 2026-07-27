---
tags:
  - asymmetric
---

1. select $p,q$ large primes (about 500 bits each)
2. $n=pq$, $\phi=(p-1)(q-1)$
3. select $e$ such that $1<e<\phi$ and $gcd(e,\phi)=1$ 
4. compute $d$ such that $ed \mod \phi = 1$ 
5. public key -> $(e,n)$
6. private key -> $d$

represent the message as an integer m in [0,n-1]

**encryption** -> $c = m^e \mod n$
**decryption** -> $m = c^d \mod n$

do to modular exponentiation we can multiple $e$ times, it inefficient
so we use [Square and Multiplu](https://www.practicalnetworking.net/stand-alone/square-and-multiply/)

scan to exponent bits left to right
1. in Every iteration we **square**
2. if current bit is 1 we also **multiply by x**

