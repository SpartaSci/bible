---
tags:
  - wireless
  - gnss
aliases:
  - GNSS
---
> GNSS provide signals from a **constellation of satellites** aiming at providing an almost **global coverage** on the Earth surface

A **position** is defined by longitude, latitude and altitude

# space segment
> GNSS satellites continuously **transmit** navigation signals in different frequencies in [L band](https://en.wikipedia.org/wiki/L_band)

These signals contain [[signal analysis/spread spectrum|spreading codes]] (*spreads the input data across a wider frequency range compared to the input frequency*) and **navigation data** to allow the users to compute the **travelling time** from satellite to receiver and the **satellite coordinates** at any [epoch](https://en.wikipedia.org/wiki/Epoch_(computing))

# control segment
> a network of station, distributed all around of the Earth in order to **monitor** the status of the satellites and of the signals  

It is important for [[wireless/GNS/Multilateration#^654c6e|synchronization]] of the satellites
# user segment
the user segment is made of a wide range of different receivers, with different performance levels.

> the receiver **estimate** the position of the user based on the signals transmitted by the satellites. The **computation** is performed on the receiver's end

core functionalities:
- identification of the satellites
- measure of the [[wireless/GNS/pseudorange|pseudorange]]
- **Position**, **Velocity** and **Time** estimation algorithms (PVT)


[[wireless/GNS/Multilateration|Multilateration]]

[[wireless/GNS/GNSS Threats#GNSS Threats|GNSS Threats]] 
- [[wireless/GNS/GNSS Threats#bandwidth size|bandwidth size]]
- [[wireless/GNS/GNSS Threats#position|position]]
- [[wireless/GNS/GNSS Threats#intentional|intentional]]
	- [[wireless/GNS/GNSS jamming|GNSS jamming]]
	- [[wireless/GNS/GNSS spoofing|GNSS spoofing]]
			 


