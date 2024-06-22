> a [[hardware/attack taxonomy/side channel/_side channel|side channel]] power attack rely on power analysis but the concept is the same of [[hardware/attack taxonomy/side channel/timing attacks|timing attacks]]

**Simple power analysis** SPA: this method involves analyzing the power consumption profile over a period of time to extract information directly. The power profile may reveal distinct patterns corresponding to specific operations.
Ad example a multiplication function consume more current than addition, indeed it can be used with the timing attacks 

May not be practical in presence of: noise, interrupts, multi-core architectures, peripheral


**Differential power analysis** DPA: this more sophisticated approach requires collecting multiple power consumption profiles.  By comparing these profiles and analyzing the differences, the attacker can identify data-dependent correlations

It takes multiple traces of two data sets and then computes the average difference of these traces
- the two traces are not correlated if the difference is close to zero
- the difference will be a non-zero number if the sets are correlated

Given enough traces, even tiny correlations can be seen, regardless of how much noise is in the system, since it will be cancel out during the averaging

Require the knowledge of the algorithm but not its physical implementation

Are cheap and easy to perform

The basic idea is to correlate the power consumed by the device and the encryption data, including the key


# countermeasure against DPA

Introduction of random process interrupts

Instead of executing all the operations sequentially, the CPU, interleaves the code's execution with that of *dummy instructions* so that corresponding operation cycles do not match because of time shifts


