---
aliases: []
---

[[wireless/WLAN - wifi/Security/802.11i|802.11i]]

One of major new features introduced in WPA3 is **simultaneous authentication of equals (SAE)**
- provide more robust password based authentication, even when the chosen password falls short of typical complexity recommendations
- given protection against complexity brute-force attacks


SAE **replaces** the [[wireless/WLAN - wifi/Security/802.11i#4-way handshake|4-way handshake]] used in WPA2, thus being robust against [[wireless/WLAN - wifi/Security/KRACK attack|KRACK attacks]]. It avoids the need of knowing a pairwise master key [[wireless/WLAN - wifi/Security/802.11i#SRN - Robust Security Network Association|PMK]] that is pre-shared.

SAE considers **devices** **equally** rather than requester and authenticator, since both entities send their authentication information independently in the SAE handshake process

SAE is based on [[crypto/Elliptic curve|Elliptic curve]] [[crypto/public key/Diffie-Hellman|Diffie-Hellman]] 


Since the PSK generated in the SAE process is for **authentication only**, SAE offers **forward secrecy**

SAE requires a new password exchange each time a connection is established

