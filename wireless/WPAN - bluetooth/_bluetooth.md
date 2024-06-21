---
tags:
  - communication
  - wireless
  - WPAN
aliases:
  - bluetooth
---
[[wireless/network/WPAN - Wireless Personal Area Network|WPAN - Wireless Personal Area Network]]

**Bluetooth** was designed as *wireless cable* more than general-purpose wireless network. It was intended to be short-range, low-power and inexpensive.
[data rates](https://content.cdntwrk.com/files/aHViPTg1NDMzJmNtZD1pdGVtZWRpdG9yaW1hZ2UmZmlsZW5hbWU9aXRlbWVkaXRvcmltYWdlXzYzMWU3ZWQ2ZTRkNjcuSlBHJnZlcnNpb249MDAwMCZzaWc9MzZjYzJmMzgwZTE5YjFhNmNlYWU5MzNiNDkzMTU3OTY%253D)


# topologies
![[wireless/network/WPAN - Wireless Personal Area Network#^e463f9|piconet]]

Slaves nodes can have a **direct connection** with the master devise **only**
This requires logical link setup [[wireless/Communications/ARQ - automatic repeat request|ARQ]] [[wireless/Communications/FEC - forward error correction|FEC]]

[[wireless/WPAN - bluetooth/piconet#piconet|piconets]] and [[wireless/WPAN - bluetooth/piconet#scatternets|scatternets]]

# bluetooth 
specifications:
- less than 10 meters diameter
- **ad-hoc** network, master slave
- 2.4-2.5 GHz radio band up to 3Mbps. Crowded band, therefore need coordination
- **Master controller**: master polls clients and grants requests for client transmissions.
	- [[signal analysis/signal multiplexing#TDM - Time Division Multiplexing|TDM]] and [[signal analysis/signal multiplexing#FDM - Frequency Division Multiplexing|FDM]]  
- **Parked mode**: client can go to sleep and later wake up
- **Bootstrapping**: node can plug-and-play automatically into piconet
- [[wireless/WPAN - bluetooth/Frequency hopping|Frequency hopping]]: devices move from one channel to another, in order to no interfere with other devices in the piconet



# BLE
Protocol stack -> [[wireless/WPAN - bluetooth/BLE - Bluetooth Low Energy|BLE - Bluetooth Low Energy]]



# BL protocol stack
Similar to the BLE one, but physical layer differs.

## PHYS
BT BR/EDR differs from BLE but **principles are the same**

Physical layer situated in the [ISM](https://en.wikipedia.org/wiki/ISM_radio_band) band from 2.4 GHZ to 2.485 GHz UHF

It is am **overloaded spectrum**, meaning that there's a lot of interference


### Physical layer characteristic

**Baseband error correction/detection**: 
- [[wireless/Communications/ARQ - automatic repeat request|ARQ - automatic repeat request]] on top of stop-and-wait
- CRC - cyclic redundancy check 
- [[wireless/Communications/FEC - forward error correction|FEC - forward error correction]] thanks to ECC error correction code

**Modulation**: [[signal analysis/modulation/analog carrier/digital data modulation#Phase Shift Key (PSK)|PSK]]

**Spread spectrum**: [[signal analysis/spread spectrum|spread spectrum]] -> [[signal analysis/signal multiplexing#CDM - Code Division Multiplexing|CDMA]]

[[wireless/WPAN - bluetooth/Frequency hopping|Frequency hopping]]


## link layer

All devices share the **master's clock**

Frame structure



# security

[[wireless/WPAN - bluetooth/bluetooth security|bluetooth security]]