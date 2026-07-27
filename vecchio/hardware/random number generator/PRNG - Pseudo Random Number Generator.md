---
aliases:
  - PRNG
  - PRN
---


> A PRNG is an algorithm or a hardware device that generates a sequence of random bits starting from an **initial value** called the **seed**


The sequence of random values **repeat periodically**, it should be very long. Its periodicity depends on the size of the *internal state model*



> [!danger] caveat
> Perfect knowledge of the generating circuit and the most recently generated numbers could enable one to guess the next number to be generated

PRNGs are often  called **Deterministic random number generators**, given a particular seed value, the same PRNG will always produce the same sequence of random numbers

**Seed** must be kept secret

# hardware PRNG
Are mostly implemented resorting to **Maximal length Autonomous Linea Feedback Shift Registers**. An [[hardware/watermarking/LFSR - Linear Feedback Shift Register|LFSR]] with no inputs and whose characteristic polynomial is *primitive* so it is capable of reaching all the possible $2^n-1$ states

To mask the fact that they are deterministic, PRNGs are often devised to generate more bits than needed.
128-bit ALFSR -> 32-bit PRNG

Protection comes from the fact that it is more difficult to discover the 96 hidden bits than the 32 bits used for the random number.
You don't know the *polynomial exact position*


# software PRNG
> mostly implemented using programs that implement a recurrence operation


**Linear congruential generator** $$X_{n+1}=(aX_n+c)\mod M$$
The number a,c and M must be carefully chosen to get a good random number generator. Involves sophisticated use of number theory, prime number 




PRNG are cyptographically insecure

[[hardware/random number generator/CSPRNG - cryptographically secure PRNG|CSPRNG - cryptographically secure PRNG]]
