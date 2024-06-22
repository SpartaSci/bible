---
aliases:
  - IP
tags:
  - hardware
---
The idea of increasing the level of abstraction is usually referred as IP-based design

**soft IP**: consists of synthesizable [[hardware/VLSI and IP/RTL - register transfer level|RTL]] code, typically written in [[hardware/VLSI and IP/HDL - hardware description language|HDL]]
**firm IP**: is partially synthesized IP, provided at gates leval as [[hardware/VLSI and IP/netlist|netlist]]
**hard IP**: fully synthesized and layout complete IP

The main approach involves collecting all the IPs, connecting them together, and then implementing the integrated circuit [[hardware/VLSI and IP/ASIC|ASIC]]


This method is widely adopted 

Any element that can be used to build a complex system can be an IP

The **advantages** are numerous. The IPs are already developed, tested, verified, and configurable. 
IPs come with everything you need: [[hardware/VLSI and IP/HDL - hardware description language|HDL]] description, constraints, performance specifications, synthesis, place and route data

This allow a **fast time-to-market** and **reduced cost**

Several factors to consider when connecting IP:
1. **Interface compatibility**: ensuring that blocks work together as expected
2. **Security**: if relying on third-part IPs, the source must be trusted to prevent leaks of sensitive information, or risks of vulnerabilities and malicious code
3. **Licensing**: if using third-part IPs, licensing agreements must be followed. This involves paying for the [[hardware/_intro/chain/Intellectual property|IP]] and potentially paying royalties per item manufactured. For large-scale these cost can add up



