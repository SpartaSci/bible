---
tags:
  - defence
---
> never let the scan chains freely accessible from the circuit pins

# countermeasures


**unbound scan chain**: using fuses, means to leave the scan chain unconnected to any specific input or output pins. 


**Built-in Self-Test BIST**: replace Scan Chains with Built-in Self-Test solutions

> [!check] pro
avoid scan-based testing
allow at-speed testing
reduced After The Event costs


> [!error] contro
area overhead
fault coverage
diagnosis




**Secure Test Access Mechanism**

> [!danger] contro
authentication (expensive)
no in-field debug/diagnosis
not easy to integrate into a design flow



**Scan Chain Encryption**: encrypting scan chain content with a secret key

> [!success] controllability and observability
> untouched if the secret key is unknown 
> impossible to control or observe otherwise

> [!danger] Constraints
 to modify the test vector and response offline



