---
tags:
  - attack
---


> a timing [[hardware/attack taxonomy/side channel/_side channel|side channel]] attack tries to recover sensible data by measuring computation time in a hardware device

In particular it looks at how long a system takes to do something and uses statistical analysis to find the target data

Variabilities that can affect the timing
- **performance optimizations**
- **branching** and **conditional** statements
- **processor instructions**
- **RAM or cache hits**



# timing analysis on [[crypto/public key/RSA|RSA]]

The modular exponentiation step in RSA encryption is done by a Square and Multiply algorithm that based on the bit value of the base do different operations

Iterating one the exponents bits left-to-right we do:
- every iteration a **square**
- only if **the bit is 1** we also do **multiply by x** 

the multiply is an extra step that require more time in respect when the bit is 0. 

By this analysis we can extract the key

