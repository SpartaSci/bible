---
tags:
  - network
aliases:
  - SDN
---
> The new idea for network architecture is that there is a single orchestrator (centralized) who decides hoe packets should be forwarded and then send the information to the routers for them to operate according to its choices  


A network device can be logically partitioned into:
- **Management plane**: user and admin configuration;
- **Control plane**: dynamic configuration of the data planes
- **Data plane**: forwarding


The **SDN** separates the control plane from the data plane and the control plane can be programmatically control several devices. 

# The four pillars of SDN

**Separate control plane from data plane**: the application logic of routing is implemented in a software application that runs on an external controller that is separated from the data plane.

**Simple data plane**: data plane has to perform traffic forwarding based on match/action paradigm. So data plane is mainly a way to create a network pipes, also called *plumbing*

**Centralized control**: the software views the entire network and can easily control it. Moreover, the SDN controller can perform also a big switch abstraction to hide internal details on the network.
The centralized controller can be a **logically centralized controller** in terms of different devices (physically separated) that perform different operations for the purpose to create the routing tables to distribute.
- **advantages**: the controller is more sca


**Context-based forwarding**: it implies that the controller can take decision at run-time, based on the actual traffic. The switch can send a packet to the controller where the controller application will determine how to handle that traffic in that specific moment based on the network traffic or other measures