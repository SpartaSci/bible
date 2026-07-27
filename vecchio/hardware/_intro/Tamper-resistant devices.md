---
tags:
  - hardware
---
# Temper-resistant devices
>Device properly engineered in a way to reduce the surface for physical attacks

Strengthening  of the hardware physical shielding:
- device built in a way that attempt to open it will damage or destroy the entire chip
- additional metallization layer on top of the actual circuit to prevent [[hardware/attack taxonomy/invasive attacks/microprobing|microprobing]]
- circuit board needs to be dipped in special material to prevent easy access

[[hardware/conterfeit/_counterfeiting|counterfeiting]] protection:
- hiding device's name and serial number to make more difficult to exploit known vulnerabilities


# Temper-evident devices
> devices that include some indicator of compromise, automatically activated when someone tries to mess with its physical integrity

**Physical level**:
- packaging should maximize the evidence of tempering.
- additional internal sensors to detect laser of [[hardware/attack taxonomy/fault attacks/_fault attacks|fault injection attack]]

**Software level**:
- appropriate auditing mechanism through logging procedures to trace conducted activities and their sources
