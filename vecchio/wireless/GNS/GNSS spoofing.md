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

In a GNSS system, a meaconing attack is performed by rebroadcasting (towards the victim receiver device) **after some time delay** previously captured legitimate satellite messages. Due to the design of GNSS systems, such kind of messages are going to affect the possibility of receiver terminals to reliably compute the position, velocity, and time coordinates. Receiver terminals indeed rely on the measured time difference between the message reception and the time of transmission by the satellite contained inside the message. Therefore, when old satellite messages are received, the time computation is inevitably going to be incorrect. **PVT calculations are going to be less accurate**, usually observing a lot of sudden jumps in the computed position.

Meaconing attacks could be detected:
- after PVT solution, by sudden jumps in computed positions
- at the physical layer, like for jamming and spoofing attacks, by different signal strength, noise, and SNR levels compared to the legitimate signals received by satellites.


# anti-spoofing techniques

**Anti-spoofing** is based on the detection of signal features that are revealing the malicious nature of the signal.
- Direction of Arrival
- cross check with other pseudoranges
- navigation message outliers of the observable

**Cryptographic spoofing defences**: encrypt or digitally sign components of the broadcast signal

**Non-cryptographic spoofing defense**: act at the receiver level