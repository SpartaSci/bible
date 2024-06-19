---
tags:
  - wireless
---
![](https://www.researchgate.net/profile/Kandarpa-Sarma/publication/271520378/figure/fig11/AS:650514534502412@1532106159545/A-Typical-Digital-Communication-System.png)

# transmitter chain
> prepares data stream to convey digital information over analog medium in a robust fashion

[[wireless/Communications/source coding|Source encoding]]: implements source encoding to limit the amount of transmitted data. Goal: **Reduce data**
[[wireless/Communications/channel coding|Channel encoding]]: implements channel encoding ([LDPC](https://en.wikipedia.org/wiki/Low-density_parity-check_code)) to limit the effect of channel disturbances. Goal: **more robust data** 
[[signal analysis/_signal#modulation|Modulator]]: **converts** the digital signal into an analog signal to be transmitted over the channel

# channel section
> the channel transfers analog signal from TX to the RX

different types if disturbance:
- frequency-domain distortion
- wireless fading
- additive noise 
- impulsive noise 
- interference from other channels


# receiver chain
**Demodulator**: **converts** the received analog signal into a sequence of sample to be processed by the decoder 
**Channel** decoding: to **limit** the effect of channels errors during the signal propagation over the medium and extract the useful information data
**Source** decoding: to **expand** the compressed data back to their original form



[[signal analysis/_signal|_signal]]
[[signal analysis/signal multiplexing|signal multiplexing]]

[[wireless/Communications/source coding|source coding]]

[[wireless/Communications/channel coding|channel coding]] -> [[wireless/Communications/error detection and correction|error detection and correction]]
