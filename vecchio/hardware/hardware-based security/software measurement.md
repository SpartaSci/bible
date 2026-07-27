---
tags: 
aliases:
  - monitoring
  - measurement
---
1. The [[hardware/hardware-based security/secure engine|SecE]], which is considered secure, built on top of hardware, starts the system
2. HW starts the hypervisor, and its code will be checked against the digitally signed version of it


When all levels are trusted, **compute cryptography hashes over code and data of each level**, defined as **measurements** to verify the #integrity and #authenticity of the components. This mechanism is at the base of [[hardware/hardware trust/TPM features/secure boot|secure boot]]

# using 
## secure boot
Abort boot when a **wrong measurement** is obtained, or continue but do not decrypt secrets

## remote attestation
Allows changes to the user's computer to be detected by authorized parties. Ad examples help companies to identify **unauthorized** changes to software, including users modifying their software to circumvent commercial digital rights restrictions (spotify)

It is usually combined with public key encryption, so the information transmitted can only be read by authorized programs and not by an [[cybersec/attacks/sniffing|eavesdropper]]

## sealed storage
Protects private information by binding it to *platform configuration information* including the software and the hardware being used

## protect from TOC-TOU
Continuous monitoring and signing, is a potential solution to [[hardware/hardware-based security/TOC-TOU|TOC-TOU]]

Constantly measure the system and look for anomalies
Requires knowing the correct and expected behavior of the system

