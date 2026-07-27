---
tags:
  - wireless
---
> transfer analog signal from TX to the RX


# problem

frequency-domain distortion

wireless fading

additive noise

impulsive noise

interference from other channels


# major source of error
**Thermal noise**: ^60ae13
- disturbs signal in an additive fashion
- has flat spectral density for all frequencies -> occupies all frequencies (white)
- is modeled by Gaussian random process

**Inter-symbol Interface (ISI)**:
- due to filtering effect of transmitter, channel and receiver, the symbols are spread 
- channel is modeled by a filter, therefore, signals are ruined by the channel that introduce unwanted 


## receiver task
In order to recover the right symbol the receiver needs to:
1. reduce noise in order to get a clear signal
2. [[wireless/Communications/_digital communication#receiver chain|Demodulation]] and [[signal analysis/_signal#nyquist theorem - sampling|sampling]]:
	1. waveform recovery and preparing the received signal for detection
	2. Improving the SNR using **matched filter**
	3. Reducing ISI using an equalizer
	4. Sampling the recovered waveform
3. Detection: estimate the transmitted symbol based on the received sample

When designing the receiver we need to find the optimum solution considering:
### Maximize SNR
We can maximize the Signal-to-Noise Ratio by following a simplified noise model
- n(t) is a **random** process, each sample of n(t) is a random variable
- its *variance* is proportional to the noise density N0
- $r(t)=s_i(t)+n(t)$ 

Therefore we need to design a filter h(t) that yields the **maximum SNR at sampling**. SNR is maximized by the match filter
$$h(t)=g(T-t)$$

### Minimize ISI
In order to minimize ISI the channel impulse response must be revered. ISI is due to filtering effect of the communications channel