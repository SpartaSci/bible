---
tags:
  - ISO-
---

Stands for **Carrier Sense Multiple Access - Collision Avoidance**

> Handles the **hidden terminal** problem, taking into consideration the also **signal attenuation**

The point is to **avoid collisions** since 2+ nodes can transmit at the same time.


# CSMA/CA
**802.11 sender** sense the channel:
- if the sense channel idle for [DIFS](https://en.wikipedia.org/wiki/DCF_Interframe_Space) then transmit entire frame, cause no Collision Detected
- if sense channel is busy then, start **random backoff** time, transmit when timer expires, if no ACK received, increase random backoff interval and repeat the process until ACK

**802.11 receiver**:
- if frame received correctly, return the ACK after [SIFS](https://en.wikipedia.org/wiki/Short_Interframe_Space). ACK is needed due to hidden terminal problem


> [!Attention] Collisions may still happen
> since the sender can't detect another sender until receiver sends back an ACK

# with RTS/CTS
> allow the sender to **reserve** the channel rather than random access of data frames, in order to **avoid collision of long data frames**

1. sender first transmits **small** request-to-send **RTS** packets to base stations using CSMA, **RTSs may still collide** with each other, but they are short
	- RTS includes source, destination, and duration **NAV** 
2. Base station **broadcasts** clear-to-send **CTS** in response to RTS. CTS is heard by all nodes, therefore the other stations defer transmission for [NAV](https://en.wikipedia.org/wiki/Network_allocation_vector) time and go to sleep to save power, while the sender transmits the data frame
	- The CTS must be sent at the basic rate so everyone can receive it correctly.
3. **Virtual carrier sense** allows a node to **reserve** the radio channel for a duration value contained in the **NAV**. Each frame contains a duration value that indicates the number of microseconds for which the channel is reserved.
	- the other nodes are allowed to transmit only when NAV reaches 0


## Attack on RTS/CTS: virtual carrier sense

A **simple NAV attack** would be to forge packets with large duration.
If CTS/RTS is in place, the AP will broadcast the spoofed NAV (reaching also nodes that didn't received the RTS of the attacker) and therefore AP and all nodes cannot transmit for the spoofed NAV duration.

### Practical NAV defense
The main hypothesis for this defence strategy is that *legitimate duration* values for NAV are relatively small. Therefor the aim is directed at **determinate maximum reasonable NAV values** for all frames, in order to enforce all nodes to respect this threshold

