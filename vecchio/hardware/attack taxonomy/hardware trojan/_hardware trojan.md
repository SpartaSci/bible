---
tags:
  - attack
  - hardware
---
> A **hardware trojan** is a malicious insertion or alteration to an integrated circuit design, with possible effects ranging from leakage of *sensitive information* to the *destruction* of the circuit itself

The changes can be inserted at any stage of the [[hardware/_intro/chain/design flow|design flow]] and [[hardware/_intro/chain/fabrication|manufacturing]] process

Main system target: military, banking, transport and telecommunication, critical infrastructure like nuclear power plants


A hardware trojan can remain silent and undetected until it is activated by a specific **trigger**. This approach ensures the trojan remains hidden preventing detection during routine check.

characteristic
- **low possibility of occurrence**: operates very infrequently
- **very small hardware overhead**: to avoid detection, limiting the delay that would be noticeable
- **extremely hard to detect**

**The challenge with detecting these trigger lies in their infrequency and specificity, which makes them less likely to be activated during [[hardware/watermarking/testing|testing]]**



# vulnerabilities in the design flow

**pre-silicon** design, test and tool: untrusted 3rd party [[hardware/VLSI and IP/Intellectual Properties|IPs]], untrusted tools, untrusted libraries ...

**silicon** untrusted [[hardware/_intro/chain/fabrication|foundry]]: malicious circuit insertions, [[electronics/Ring oscillator|Ring oscillator trojan]], [[hardware/_intro/hardware vulnerability#^f591a4|backdoor circuits]]

**post-silicon** malicious packaging elements: disguise a [[hardware/conterfeit/_counterfeiting|malicious chip]] as a legitimate one

[[hardware/attack taxonomy/hardware trojan/trojan in the chain|trojan in the chain]]

# structure
[[hardware/attack taxonomy/hardware trojan/payload|payload]]

[[hardware/attack taxonomy/hardware trojan/trigger|trigger]]


[[hardware/attack taxonomy/hardware trojan/classification trojan|classification trojan]]

[[hardware/attack taxonomy/hardware trojan/trojan detection|trojan detection]]

[[hardware/attack taxonomy/hardware trojan/trojan mitigations|trojan mitigations]]

