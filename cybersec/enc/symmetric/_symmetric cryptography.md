---
tags:
  - symmetric
  - confidentiality
aliases:
  - symmetric
---
> only a single key is shared by the sender and receiver






# possible attacks

**ciphertext-only attack**: the adversary can only observer ciphertext produced by the same encryption key
**known-plaintext attack**: the adversary can obtain corresponding plaintext-ciphertext pairs produced with the same encryption key
**adaptive chosen-plaintext attack**: the adversary can choose plaintext and obtain the corresponding ciphertext
**adaptive chosen-ciphertext attack**: the adversary can choose ciphertext and obtain the corresponding plaintext
**related-key attack**: the adversary can obtain ciphertext or plaintext-ciphertext pairs that are produced with different encryption keys that are related in a know way to a specific encryption key

# exhaustive key search attack
> given a small number of plaintext-ciphertext pairs encrypted under a key K, K can be recovered by exhaustive key search with $2^{K-1}$ processing complexity


# ciphers

**Caesar cipher**: substitution cipher that maps each letter with a number n, such that the substituted letter is represented by the number $n+k \mod z$ 

**Mono alphabetic cipher**: maps each plaintext letter to a distinct ciphertext letter

**One-Time Pad**: single pre-shared key that is larger than or equal to the size of the message being sent. Produce a **random output** that bears no statistical relationship to the plaintext. Offers complete security but problems of making large keys and distributing large keys
[[cybersec/enc/symmetric/stream/_stream cipher|_stream cipher]]

