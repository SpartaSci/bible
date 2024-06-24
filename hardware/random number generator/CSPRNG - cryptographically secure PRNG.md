

There are two primary requirements for a [[hardware/random number generator/PRNG - Pseudo Random Number Generator|PRNG]] to be a SCPRNG

**Satisfy the next-bit test**: if someone knows all k bits from the start of the PRNG, they should be *unable* to predict the bit k+1 using reasonable computing resource

**Withstand the state compromise extensions**: if an attacker guesses the internal state of the PRNG or it is revealed somehow, they should be *unable* to reconstruct all previous random number before the revelation


Most CSPRNGs use a combination of entropy from the OS (like a [[hardware/random number generator/TRNG - True Random Numbers generators|TRNG]]) and high-quality [[hardware/random number generator/PRNG - Pseudo Random Number Generator|PRNG]]. The new entropy is used to **re-seed** the PRNG to change the internal state 

This constant reseeding over the time makes the CSPRNG really hard to predict and analyse


