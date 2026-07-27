---
tags:
  - attack
---

# vulnerability exploitations

1. Identify the **target FFs** that contain the secret to be stolen
2. Identify the **scan chain** SC to which the target FFs belong
3. Identify the precise **time instant T** in which the target FFs contain the secret.
	1. this can be hard if timing countermeasures are present
4. Run the circuit in **Normal mode** until the time T
5. **Stop** the circuit and switch it to **Test mode**
6. **Scan out the content** of the scan chain SC until the content of all the target FFs reach an output point you can observe
7. if Test de-compressors and compressors are present, you have to **reverse** them previously

