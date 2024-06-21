
[[wireless/WPAN - bluetooth/_bluetooth|bluetooth]]

BLE was standardized in 2009. Aimed to novel application requiring low energy constraints

It is **independent** of classic Bluetooth and has **no backward compatibility**. It provides considerably reduce power consumption, achieving it by sleeping for long intervals between connections

![](https://miro.medium.com/v2/resize:fit:1400/1*7R_hkwuk8v7gClsVXtoqPw.png)
# Host part
The host part which is more related to the **software side** is composed of different components

## GAP

**Generic Access Profile**: specifies roles, modes and procedures of a device
- it offers a communication channel for 2 devices that want to communicate
- it manages the **connection establishment** and **security**

Possible device states:
- **Standby**: the device is in the initial idle sate upon reset
- **Advertiser**: the device is advertising with *specific data* (name,address,...), letting any initiating devices know that it is a **connectable devices** (it becomes the slave)
- **Scanner**: when receiving the advertisement, the scanning device send a *scan request* to the advertiser. *Device discovery* 
- **Initiator**: when initiating, it must specify a **peer device address to which connect** sending a *request to establish a connection*. (It become the master)
- **Slave/Master**: connection is formed


## GATT
**Generic attribute**: allows devices to communicate with each other by providing data **communication** between 2 **connected devices**

Uses *client-server architecture*:
- **GATT-client**: *initiates* commands and *requests* toward the server, and receive response, indications and notifications .
- **GATT-server**: *Accept* incoming commands and requests from a client and send *responses*, indications and notifications

Other GATT terminology:
- **service**: a *collection of data* and associated *behaviours* used to accomplish a particular function or feature
- **characteristic**: contains the *value* used in a service along with appropriate permissions
- **descriptor**: a *description* of the associated characteristic

## ATT
**Attribute**: transfers **single attribute** data between clients and servers in GATT-based profiles
It defines a set of rules guiding **how data is accessed**

## L2CAP

**Logical Link Control and Adaptation layer Protocol**: *encapsulates* data from the BLE higher layer into standard BLE **packet format** for transmission according to the link configuration.
It performs protocol [[signal analysis/signal multiplexing|multiplexing]], segmentation and reassembly, re-transmission ([[wireless/Communications/ARQ - automatic repeat request|ARQ]]) and flow control

# middle ware layer

The SDP **service discovery protocol**: allows a device to **discover services** offered by other devices and their associated **parameters**
# controller part
The controller-side **host controller interface HCI**:
- handles the interface between host and controller
- **Defines** a set of **commands** and **events** for transmission and reception of packets data
- When receiving packets from the controller, HCI **extracts raw data** to send to the host 

## link layer
Works like the MAC layer of the OSI model and manages the link state of the radio to **define the role** of a device

## LE PHY
Is the air interface that offers the transmission services

