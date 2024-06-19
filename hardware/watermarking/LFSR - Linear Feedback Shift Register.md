---
tags:
  - hardware
aliases:
  - LFSR
---
A set of flip-flop connected as a shift register but with XOR gates combining the output of some FFs to create a feedback

The possible configuration of an n-bit LFSR are $2^n$ 

if it is initialized with all zeros it never changes its state

otherwise it can reach up to $2^n-1$ (all, except all zero)

Not all LFSR configuration can reach $2^n-1$, only if the corresponding polynomial is primitive

