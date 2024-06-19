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

These signals contain **spreading codes** ([*spreads the input data across a wider frequency range compared to the input frequency*](https://www.ni.com/en/solutions/aerospace-defense/communications-navigation/understanding-spread-spectrum-for-communications.html)) and **navigation data** to allow the users to compute the **travelling time** from satellite to receiver and the **satellite coordinates** at any [epoch](https://en.wikipedia.org/wiki/Epoch_(computing))

# control segment
> a network of station, distributed all around of the Earth in order to **monitor** the status of the satellites ans of the signals  

# user segment
the user segment is made of a wide range of different receivers, with different performance levels.

> the receiver **estimate** the position of the user based on the signals transmitted by the satellites. The **computation** is performed on the receiver's end

core functionalities:
- identification of the satellites
- measure of the [[wireless/GNS/pseudorange|pseudorange]]
- **Position**, **Velocity** and **Time** estimation algorithms (PVT)


[[wireless/GNS/Multilateration|Multilateration]]
![[wireless/GNS/Multilateration#def|Multilateration]]


# threat
![[wireless/GNS/GNSS Threats|GNSS Threats]]
