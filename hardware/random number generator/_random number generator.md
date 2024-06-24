---
tags:
  - hardware
  - encryption
aliases:
  - RNG
---


> the process of generating random quantities is usually called *Random Number Generation*. This involved hardware or software modules are called **Random Number Generator**

> A **RNG** is utility or device that produces a sequence of number within an interval [min,max] while guaranteeing that values appear unpredictable

**Characteristics**:
- each value must be **statistically independent**
- the overall distribution of numbers chosen from the interval id **uniformly** distributed
- sequence must be **unpredictable**


[[hardware/random number generator/TRNG - True Random Numbers generators|TRNG]]
[[hardware/random number generator/PRNG - Pseudo Random Number Generator|PRNG]]

[[hardware/random number generator/CSPRNG - cryptographically secure PRNG|CSPRNG - cryptographically secure PRNG]]


# conceptual model
Problem: we need to generate K random values
Assumption: we can rely on the availability of N values (N>>K). The **pool**
Solution: we generate the K values extracting them out of the pool

