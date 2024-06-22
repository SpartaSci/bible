---
tags:
  - attack
  - hardware
---
> the act of exploiting a hardware [[hardware/_intro/vulnerability|vulnerability]] to perform an attack


# goal
**steal** a target (crypto key, secret password, [[hardware/VLSI and IP/Intellectual Properties|IP]]) [[cybersec/_properties/confidentiality|confidentiality]]
**corrupt** a target (memory, permission file, function) [[cybersec/_properties/integrity|integrity]]
**inhibit** a target (service, set of data, defence) [[cybersec/_properties/availability|availability]]

# target
**information** treated by the hardware (key, memory word, file)
**property** owned by the hardware ([[hardware/VLSI and IP/Intellectual Properties|IP]], resource, functionalities)
# domain

**logical**: carried out exploiting the *software* run by the hardware
**physical**: carried out directly exploiting a hardware [[hardware/_intro/vulnerability|vulnerability]]

# modality

[[hardware/attack taxonomy/invasive attacks/_invasive attacks|invasive attacks]] 
- [[hardware/attack taxonomy/invasive attacks/microprobing|microprobing]]
- [[hardware/attack taxonomy/invasive attacks/reverse engineering|reverse engineering]]
- [[hardware/attack taxonomy/invasive attacks/data remenance|data remenance]]

**non-invasive** carried out without physical contact with the device under attack
- **passive**: carried out by analyzing and measuring one or more physical dynamic entities of the attacked hardware
	- [[hardware/attack taxonomy/side channel/timing attacks|timing attacks]]
	- power attacks
	- electromagnetic attacks
	- acoustic attacks
	- optical attacks
- **active**: require specific actions on the device to force the system into abnormal states in which is more vulnerable
	- [[hardware/attack taxonomy/fault attacks/_fault attacks|_fault attacks]]
	- [[hardware/attack taxonomy/test-infrastructure/_test-infrastructure-based Attacks|_test-infrastructure-based Attacks]]



