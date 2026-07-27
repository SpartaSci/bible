---
tags:
  - hardware
  - attack/active
aliases:
  - fault attack
---
[[hardware/attack taxonomy/_hardware attack taxonomy|_hardware attack taxonomy]]

> consist in [[cybersec/attacks/injection|injecting]] deliberate (malicious) fault into the target device, aimed at bringing it into a set of states from which private internal information items can be fraudulently extracted

**temporary**: they change the content of something for a while and can be restored

**permanent**: are there forever, and do not clear

**How does it work**: injection forces a 0 on a single bit of the secret key, **we do not know the key** but we know we have forcing a bit in a specific position. Then we try tu decrypt and it does correctly means that at that position **there was actually a 0**. Repeat for all the bits

# how to inject

**under-powering** or **over-powering**

altering the **clock**

altering the **temperature**

**optical/electromagnetic attacks**: lasers can be used to change transistor states and infer energy levels. Requires de-packaging and in this sense become more a [[hardware/attack taxonomy/invasive attacks/_invasive attacks|invasive attacks]]. harmonic signals can be used too  


# goals

**bypassing** access control verification

**generating faulty** encryption/signature

**DoS**


# differential fault analysis

A set of **multiple injections** with subsequent **correlated analysis** of the faulty behavior of the target device

The attacker focus on the fault influence of the specific hardware implementations to collect some faulty output

DFA is a powerful tool for attacking cryptography systems



[[hardware/attack taxonomy/fault attacks/countermeasures to fault attacks|countermeasures to fault attacks]]



