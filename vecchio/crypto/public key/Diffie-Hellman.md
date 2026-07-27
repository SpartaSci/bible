---
tags:
  - asymmetric
---
1. **Public Parameters**: Alice and Bob agree on a large prime number $p$ and a base $g$.
2. **Private Keys**:
    - Alice selects a private key $a$.
    - Bob selects a private key $b$.
3. **Public Keys**:
    - Alice computes her public key $A = g^a \mod p$ and sends it to Bob.
    - Bob computes his public key $B=g^b \mod  p$ and sends it to Alice.
4. **Shared Secret**:
    
    - Alice computes the shared secret $S = B^a \mod p$.
    - Bob computes the shared secret $S = A^b \mod p$.

Both Alice and Bob now share the same secret $S = g^{ab} \mod p$, which can be used for secure communication.




