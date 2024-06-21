# source of attack
**Untrusted software** running on the processor [[hardware/hardware-based security/TCB - trusted computing base#^37e331|bugs in TCB]]
**Physical attacks** on the memory ([[hardware/PCB/_PCB - printed circuit board#^900a18|PCB]])
**Malicious devices** using DMA, direct access to memory (without go through the CPU)



# Types of Attacks on Memory
[[cybersec/attacks/snooping|snooping]]
[[cybersec/attacks/spoofing|spoofing]]
[[cybersec/attacks/splicing|splicing]]
[[cybersec/attacks/replay|replay]]
[[hardware/attacks/disturbance|disturbance]]


# protection

## confidentiality protection with encryption

The contents of the memory can be protected with [[cybersec/defence/encryption|encryption]] techniques in order to provide #confidentiality 

- **Data going out of the CPU are encrypted** by an *encryption engine* (usually [[cybersec/enc/symmetric/block/AES|AES]] in CTR)
- **Data coming from the memory are decrypted** by an *decryption engine* 

It is possible have a channel for plaintext, this comes with a trade-off between **time and power consumption** and **attack surface size**

The more data is encrypted the more time and power is consumed, but the smallest is the attack surface, since everything is encrypted attackers don't know where to start looking for.

Enc and Dec **must not leak any data**. It is more secure place the engine very close to the CPU, if not in the CPU Soc already. Maybe with a crypto accelerator

## integrity protection with hash tree
By using a [[cybersec/defence/merkle Tree|merkle Tree]] just by checking the root node hash value we can check for #integrity and #authentication. 
In the leaves we can place the data block's content of memory.

Moreover if the root hash value is incorrect, by reconstructing the tree it is possible to understand **which portions** of the memory were altered.

If the (sub) hash trees are not protected, both the data sections and the hash trees can be altered. **On-chip cached nodes** are assumed trusted and used to speed up verification. Counter are included in hashes for *freshness*   

MAC can be used and a smaller [[cybersec/defence/merkle Tree#Bonsai Merkle hash trees|Bonsai tree]] can be constructed.

They can consider whole memory or parts of it. Also external storage


## memory access pattern 
[[snooping|snooping attack]] can target extracting data (protected with encryption) or extracting access patterns to learn *what a program is doing*

It is easier in [[hardware/hardware-based security/SMP - symmetric multiprocessing|SMP - symmetric multiprocessing]] due to shared bus

**Access pattern** can be protected using **Oblivious RAM** such as [[hardware/hardware-based security/memory/path ORAM|path ORAM]]

> Oblivious RAM changes the way memory is accessed and organized by solving the addressing using a **one-way function** such that the mapping is not revertible for attackers



# consideration 
Security consideration about: [[hardware/_type of memory/NVM - non volatile memory|NVM]] 

**data remanance**