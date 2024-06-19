> never let the scan chains freely accessible from the circuit pins


![[_record/Recording 20240606174724.webm]]


countermeasures:
## leave the scan chain unbound
- using fuses
## Built-in Self-Test
>replace Scan Chains with Built-in Self-Test solutions

> [!check] pro
avoid scan-based testing
allow at-speed testing
reduced ATE costs


> [!error] contro
area overhead
fault coverage
diagnosis


![[_record/Recording 20240606175242.webm]]



## Secure Test Access Mechanism

> [!danger] contro
authentication (expensive)
no in-field debug/diagnosis
not easy to integrate into a design flow


![[_record/Recording 20240606175600.webm]]


## Scan Chain Encryption

encrypting scan chain content with a secret key
controllability and observability
- untouched if the secret key is knwo 
- impossible to control or observe otherwise


> [!danger] Constraints
 to modify the test vector and response offline


![[_record/Recording 20240606175959.webm]]

![[_record/Recording 20240606180129.webm]]

