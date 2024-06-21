---
tags:
  - wireless
  - gnss
---
[[wireless/GNS/_Global Navigation Satellite Systems|GNSS]]

GNSS system can be attacked by **degrading the navigation signal** and main sources of it are:
- **evil waveforms**: distortions of the broadcast signal due to failures in the onboard satellite payload
- **Multipath**: if the signal is reflect multiple times, computing the exact position becomes a problems
- Radio frequency interference **FRI**
- **Spoofing**


The robustness of GNSS signal derives from the [[signal analysis/spread spectrum|spread spectrum]] nature of the transmitted signal.
The received signal power is extremely low, **the noise** at GNSS signals bandwidth **is more powerful than the signal itself**


The **de-spreading operation** made at the receiver spreads **the power of the interfering signal** over a wide bandwidth


# interference classification

## bandwidth size

**Narrow Band**: $B_i<<B_{GNSS}$

**Wide Band**: $B_i \simeq B_{GNSS}$

**Continuous Wave**: pure tone $B_i \to 0$

**Pulsed Interface**: $DC=PRF*PW$ 
- Pulse Width PW: duration of a pulse
- Pulse repetition frequency PRF: number of pulse per seconf
- Duty Cycle: percentage of time occupied by pulse


## position
**Out-of-band interference**: interference carrier frequency close to the GNSS band. Theoretically it should not affect GNSS signals

**In-band interference**: interference carrier frequency within the GNSS frequency band


## intentional
**Unintentional interference**: out-of-band versus in-band harmonics. E.g. DVB-T transmitter

**Intentional interference**: not only related to a military context
- [[cybersec/attacks/jamming|jamming]]
- [[wireless/GNS/GNSS spoofing|GNSS spoofing]]
- 

