---
tags:
  - standard
  - wireless
  - communication
---
> IEEE 802.11 is part 802, the IEEE standard for wireless communication (WLAN)

[[wireless/WLAN/WIFI|WIFI]]

It offer **half-duplex** communication channel and works on 2.4 GHz [ISM](https://en.wikipedia.org/wiki/ISM_radio_band) and 5 GHz [U-NII](https://en.wikipedia.org/wiki/Unlicensed_National_Information_Infrastructure) bands. 


Before a mobile station can  send traffic through an AP, it must be in the appropriate **connection state**:
- not authenticated or associated
- authenticated but not yet associated
- authenticated and associated

> Data exchange can only happen after the authentication and association are completed using the [[wireless/WLAN/CSMA-CA|CSMA-CA protocol]]


1. **Beacons** are frames **broadcast** (at regular intervals) by the AP in order to advertise the SSID of the WLAN to wireless clients. ^e1b824
2. **Probes** are frames used by STA in order to find a WLAN network
	- frames are send on multiple channels
	- contains SSID of the WLAN the client wants to join and supported bit rates
		- a client can send out a *probe request* with no SSID specifications but will respond only APs without broadcast SSID disabled
	- the *probe response* includes SSID, supported data rates and security standard 
3. Once a WLAN is found, the STA performs **Authentication and Association** processes for establishing the data link with AP
4. An STA must **first** authenticate with **one or more** APs ([[wireless/network/WLAN - Wireless Local Area Networks#^244be9|ESS]])
5. after, the STA associated with **one and only one** AP


# authentication
802.11 authentication is the first step in network attachment, it requires a mobile device to establish its identity with an AP.
No data encryption or security is available in this stage. It is initiated by the mobile device.

> Authentication in 802.11 is an **open system authentication** and it follows a **shared key authentication** paradigm

1. an *authentication request* is sent from the STA that contains the station ID, typically the MAC address
2. an *authentication response* from the AP with a success or failure message
Shared key authentication: a shared key, or passphrase, is manually set on both the mobile device and the AP. ([[wireless/WLAN/Security/WEP - Wired Equivalent Privacy|WEP]],[[wireless/WLAN/Security/802.11i|WPA]])

# association
>once authentication is complete, a mobile devices ([[wireless/WLAN/WIFI#^1de188|STA]]) can associate and register with **one** AP to gain full access to the network.

Allow the AP to record each mobile device so that frames are properly deliverd. 
Association only occurs on **wireless infrastructure networks**, not in peer-to-peer mode.

1. STA sends an *association request* 
2. AP processes the request and **decides** if a client should be allowed
3. when AP approves association, it *response* with a status code of 0 and the Association ID (AID). AID is used to identify the station for delivery of buffered frames when power-saving is enabled



# CSMA/CA


[[wireless/WLAN/CSMA-CA|CSMA-CA]]



# advanced capabilities

**Rate adaptation**: base station and mobile station dynamically change transmission rate as mobile moves, SNR varies
- as node move away from base station, [SNR](https://en.wikipedia.org/wiki/Signal-to-noise_ratio) decrease, while [BER](https://en.wikipedia.org/wiki/Bit_error_rate) increases
- when BER becomes too high, switch to lower transmission but with lower BER

**Power management**: 
- node inform AP that is going into *sleep mode* until next **beacon** frame
- AP knows not to transmit frames to this node, and will buffer them. Node will wake up before next **beacon** frame

**TIM** (traffic indication map) is a period packet sent by AP (with the [[wireless/WLAN/IEEE 802.11|beacon]]) to notify client of buffered data, stating to which nodes the AP needs to send data, therefore, those nodes need to stay awake, it relies on synchronization of packets so client is awake then the TIM is sent.


# power saving attacks


There are 3 possible attacks on Power Saving:
- attacker can **spoof on behalf of the AP the TIM message**: client could think there is no data for itself and therefore it can go to sleep
- attacker **forges management synchronization packets**, this will cause the client to fall out of synchronization with the AP
- attacker **spoofs itself on behalf of the client**, AP will send data while the client is sleeping. Meaning that the attacker will forge the message that the specific attacked node is not sleeping, when in reality it is, therefore, packets directed to it will not be processed.


The attacker impersonates the victim station, this is possible as it only needs to know the AP and the victim MAC address.
The attacker keeps **injecting false Power Management frames** with the bit set to 1, therefore the AP believes the victim is in sleep mode and starts buffering the packets.
The AP sends a **beacon** frames with the **TIM** to signal the victim node to wake up, but the victim **ignores** those TIMs since it is **not in power management**

In conclusion:
- DoS attacks in 802.11 are very plausible with existing equipment
- De authentication attack is still a concern
