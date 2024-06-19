---
tags:
  - attack
  - replay
---
Key Re-installation Attack target the [[wireless/WLAN/Security/802.11i#4-way handshake|4-way handshake]] 
- in normal operation when a client joins a network and triggers the handshake, a key is [[wireless/WLAN/Security/802.11i#^f6fffd|installed]] after receiving the message 3 
- Message 3 may be re-transmitted multiple times due to unreliable network conditions
- Each time the client receives a copy of message 3, it re-installs the same **session key** with incremental nonce and a replay counter used by the encryption algorithm
- Any attacker can force nonce resets by collecting and replying message 3
- with nonce resets an attacker can decrypt packets and launch attacks such as [[cybersec/attacks/replay|replay attacks]] and forcery

KRACK may also be launched against [[wireless/WLAN/Security/802.11i#SRN - Robust Security Network Association|group keys]] in WPA2



Firstly the weakness lies in the fact that after the AP passes by sending message 3 the MIC check, the client **already trust** the AP and installs the PTK. Therefore, **the plaintext re-transmission of the 3rd key installation message** is of the utmost importance in this attack

1. the adversary uses a channel-based MITM attack so it can **manipulate handshake** message. Specifically, its intent is to **block message 4** from arriving  at the *authenticator* AP
2. immediately after sending message 4, the *victim (client)* will install PTK and GTK. At this point, the victim opens the 802.1x port and starts transmitting data frames
3. The *authenticator* since it didn't receive message 4, will **re-transmit message 3**
4. The MITM **forwards the re-transmitted message 3** to the victim, causing it to **reinstall the PTK and GTK**
	- A result, it resets the nonce and replay counter used by the data-confidentiality protocol
	- note that the adversary cannot replay an old message 3, 



# AAA da finire che due palle madonna
