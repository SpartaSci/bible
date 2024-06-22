---
tags:
  - hardware
aliases:
  - PCB
---
> are object that carry electronic devices, connecting them together


PCB **characteristic**:
- non conductive support
- mechanical robustness 
- electrically connect components

# PCB type

**single-sided PCB**: with one side for components, and the other side for routing.

**double-sided PCB**: both sides are used for placing and connecting components. Offering more flexibility

**multilayer PCB**: used for complex system with numerous elements and circuits. The board thickness increases.


frequently used serial communication protocols 

[[UART]] [[I2C]] [[SPI]] [[hardware/PCB/JTAG|JTAG]]



# good practises

**encryption**: implement encryption techniques to prevent information leakage, especially with the JTAG protocol.

**authentication**: Use private instructions in you FSM, requiring a key to 
access internal functions

**Physical access restriction**: increase PCB design resilience against [[hardware/attack taxonomy/invasive attacks/reverse engineering|reverse engineering]], [[hardware/attack taxonomy/invasive attacks/microprobing|microprobing]], [[hardware/_intro/tampering|tampering]]([[hardware/_intro/Tamper-resistant devices|Tamper-resistant devices]]) making difficult to access the pins of the IC. 
Example:  ^900a18
- use BGA (ball grid array)
- place delicate information-carrying wires inside the board (multilayer) 


> [!success] these approaches reduce risk of physically leaking information


## obfuscation techniques

### permutation networks

>Add a component to connect chips correctly only with a certain key 
([[cybersec/attacks/trojan|trojan]] link per il futuro)


### dummy ICs

You can place a second identical element in your system that does nothing but generate random information. **This increases system complexity, power consumption and cost.**

The critical aspect is ensuring that the dummy IC closely mimics the functional one, making it **difficult** for the attacker to **identify which is which**
