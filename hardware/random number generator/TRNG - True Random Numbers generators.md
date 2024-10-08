---
tags: 
aliases:
  - TRN
  - TRNG
---
> TRNGs produce a stream of truly random numbers 

Often called **non-deterministic random number generators**, utilizing source of *entropy*

TRNGS extract randomness (**entropy**) from a physical source of some type and then use it to generate random numbers

Based on analog property

>**whitening**: the process of combining the output of the TRNG with the output of a [[hardware/watermarking/LFSR - Linear Feedback Shift Register|LFSR]] increases the variance, and randomness


The analog source rely on amplifying the noise generated by a resistor or by a semiconductor diode


Alternative implementations rely on measuring *internal computer activities* that are quantifiable and genuinely random



> [!attention] They are inefficient
> Require time to reach a good entropy
