---
tags:
  - attack
---

Thermal covert channel in [[hardware/VLSI and IP/FPGA|FPGAs]]:
- cloud FPGAs allow for the sharing of FPGA resources among users
- this can lead to covert channels and information leakage

example:
- to transmit information simple **on-off keying OOK** is used
- sender and receiver share or can access the same set of FPGAs
- High temperature = 1
- Low temperature = 0

