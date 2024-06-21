---
tags:
  - gnss
  - attack/active
  - wireless
---
[[cybersec/attacks/spoofing|spoofing]]

> **Spoofing** refers to the transmission of fraudulent GNSS-like signals, that force the victim receiver to compute erroneous positions.

It is more malicious than [[wireless/GNS/GNSS jamming|GNSS jamming]] as the **false signals may take control** of the target receiver and victim is fooled without any notice.


**Potential threats** and major concerns for **liability-critical and payment-critical applications**: information about user's position or velocity is used at the basis for **legal decisions or economic transactions**

# radio frequency spoofing attack
Based on the transmission of fake GNSS signals:
- *re-transmission* of real GNSS signal
- generation of signals by means of *GNSS signal generators*

An ideal spoofer must be as much as possible consistent with the real signals 


# meaconing
[[cybersec/attacks/replay|meaconing]] is the reception and re-broadcasting of an entire block of RF spectrum (containing GNSS signals) without distinction between different satellite signals
- it can add a *variable delay*
- typically, with *higher power to cover* the true signal
- difficult to counteract, especially for near zero delay
- 

# anti-spoofing techniques

**Anti-spoofing** is based on the detection of signal features that are revealing the malicious nature of the signal.

**Cryptographic spoofing defences**: encrypt or digitally sign components of the broadcast signal

**Non-cryptographic spoofing defense**: act at the receiver level