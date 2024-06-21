---
tags:
  - wireless
---
# piconet
A piconet is defined as a network topology in which a **master** with up to **7 slaves**.
The **communication** is between the master and **one slave at time**, and the master controls everything

[[wireless/WPAN - bluetooth/_bluetooth|bluetooth]]

# scatternets

>**Scatternets** are defined as **overlapping piconets**. 

Slaves can be part of multiple piconets:
- a **slave** in one piconet can be a **master** in another
	- this link allow communication *between piconets in Scatternets* 
- a **slave** in one piconet can be a **slave** in another
- a **master** in one piconet **can't be** a **master** in another

