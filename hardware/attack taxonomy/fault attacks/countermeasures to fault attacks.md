---
tags:
  - hardware
---

**attack prevention**

**fault injection detection**: 
- laser/light sensors
- **bulk current sensors**, used to detect laser injection faults. This are used to trigger a flush code eraser to prevent the attack
- **glitch detectors**

May generate false positives


**error detection due to fault effect**
- space redundancy
- information redundancy
- time redundancy

**error detection code EDC**: 
- output code prediction
- code calculation: this step introduce delay
- generally the more we want to protect, the larger the are dedicated to EDC is



**de-synchronization**: a fault injection requires precise timing to be effective and adding temporal randomness makes the timing of the fault harder to set
- jittered clock
	- dummy instructions that create delay or do nothing
- randomized operation flow


**robust package**: several fault injection techniques require the die to be exposed, so hardening the package can help
- [[hardware/_intro/Tamper-resistant devices|Tamper-resistant devices]]
- [[hardware/_intro/Tamper-resistant devices#Temper-evident devices|Tamper-evident devices]]
