---
tags:
  - symmetric
  - encryption
---
Some principles:
- **Confusion**: relationship between plain and cipher text is obscured *substitution table*
- **Diffusion**: the influence of one each plaintext bit is spread over many ciphertext bits *permutation*


[Material](https://en.wikipedia.org/wiki/DES_supplementary_material)
[[crypto/images/des_1.png|macro block]]: 56 bits key, 64 bits input output
[[crypto/images/des_2.png|rounds]]:  Initial Permutation + 16 rounds + Final Permutation (FP=IP^-1)
[[crypto/images/des_3.png|feistel round]]: left side is encrypted
[[crypto/images/des_4.png|f function]] 32 bits from right side + 48 bits from key

the 8 S-box (Substitution blocks) are all different
[[crypto/images/expansor.png|expansion block]]
[[crypto/images/permutation.png|permutation]]



# DES

key length only 56 bits

# 2DES
key effectively 57 bits

# 3DES

key = 112 
