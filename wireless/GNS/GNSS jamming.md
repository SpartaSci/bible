---
tags:
  - attack/active
  - DoS
  - communication
  - wireless
---


[[cybersec/attacks/jamming|jamming]]

# jamming in [[wireless/GNS/_Global Navigation Satellite Systems|GNSS]]

Jamming's objective is **Denial of navigation services** by masking GNSS signals with noise.

Mass-market jammers usually aim at disturbing a wide band by [[signal analysis/modulation/analog carrier/analog data modulation#Frequency Modulation (FM)|frequency-modulating]] a pure tone


# methods to detect Jamming



## signal-to-noise monitoring

The interference can be modeled as an **additional contribution to the noise** variance. 
The receiver assumes that only **degrading source** is *uncorrelated thermal noise*
The receiver can define a statistical **threshold** based on $C/N0$ parameters

## spectral analysis 
The GNSS signal is weak and usually its spectrum is centered on the IF frequency at 4.1302 MHz.
When there’s interference it can be detected by looking at variations in the spectrum of the received signals.

## automatic gain control behavior
The main role of the **AGC** is to amplify or attenuate the input signal to **adapt** its amplitude to the *optimal input range* of the ADC

The ACG can also be a valuable tool for assessing the operating environment for GNNS receiver:
- in *absence of interference* the **gain** introduced by the AGC is almost **constant** over time
- in a *hostile environment* the average gain level is **lower** and not constant 
- if the gain becomes low, a very powerful signal was received, which may imply that the received signal is not a pure GNSS signal anymore

## goodness-of-fit test

The **goodness-of-fit test** performs the comparison of 2 probability density function allowing the decision between 2 hypothesis
1. If the [[wireless/Communications/Channel section communication#^60ae13|thermal noise]] is dominating the samples distribution, the histogram should exhibit a **Gaussian shape**
2. in presence of interference source, the histogram will **modify** its regular shape, enabling the test to **detect** such distortion


## machine learning

The model is then **trained** based on the detected jamming signals reported in literature and **perform feature extraction** from the raw samples collected after ADC at the front end

# mitigation

## notch filter
Is a type of band-stop filter, which is a filter that **attenuates** frequencies within a **specific range** while passing all other frequencies unaltered

The **adaptive notch filter** can be used against **swept frequency jammers**

## time domain pulse
**Digital pulse Blanking** can be used to remove pulsed interference acting on the time domain

