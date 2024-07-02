---
tags: 
aliases:
  - Galois Field
---
> A field is a set of numbers in which we can add, subtract, multiply and divide

In cryptography we almost always need **Finite** sets


> [!NOTE] Finite Field only exist if $p^m$ elements
> p prime, m integer

FF of 11 elements -> $GF(11^1)$
FF of 81 elements -> $GF(81)=GF(3^4)$
FF of 256 elements -> $GF(256)=GF(2^8)$ ([[crypto/symmetric/block/AES|AES]])
FF of 12 elements -> $12= 2^2 3$

**Prime fields** m = 1
**Extension fields** m > 1

[[crypto/Prime Field Arithmetic|Prime Field Arithmetic]]
