---
tags:
  - hardware
  - attack/active
---

> consist in injecting deliberate (malicious) fault


memory component
fault = changing something inside the memory, register or 


fault temporary -> it do not stand forever

permanent -> the change will stay forever

depending by the technique

i you force to 0 and after you try to put a 1, it will remain 0

if the fault is not changing 


you force 0, don see change in output -> so the content was 0

error detection


![[_record/Recording 20240606162248.webm]]

![[_record/Recording 20240606162402.webm]]

you can detect the fault but you have to stop

in the tolerance -> you can detect and correct the fault




# error detection code 


![[_record/Recording 20240606162856.webm]]

![[_record/Recording 20240606162929.webm]]


# de.syn+


![[_record/Recording 20240606163056.webm]]


a fault injection requires precise timing to be effective
Adding temporal randomness makes the timing of the fault harder to set
how to: 
- jittered clock
- dummy instructions
- randomized operation flow


![[_record/Recording 20240606163602.webm]]


![[_record/Recording 20240606163928.webm]]
## hardened IC Package

>Several fault injection techniques require the [die](https://en.wikipedia.org/wiki/Die_(integrated_circuit)) of the IC to be exposed
FIB, laser...

Hardening the package can be a #countermeasure

# importante riascoltare la lezione 

![[_record/Recording 20240606164432.webm]]

