# Solution

The categories of firewall can be compared as opposites and include the following:
- Open source vs. proprietary
- Hardware vs. software
- Host vs. appliance vs. virtual.


## Open source vs. proprietary

Some firewalls are freely available (open-source firewalls) while other firewalls are owned by an entity that has an exclusive right to them (proprietary firewalls).

Open-source firewalls have gained wider acceptance as are built on a secure foundation, but typically they incorporate less features

## Hardware vs. software
A software firewall runs as a program or service on a device

Hardware firewalls are specialized separate devices that inspect traffic.
They are specialized devices: hardware firewalls tend to have more features but are more expensive and can require more effort to configure and manage.

Disadvantage of a software firewall is that a malware infection on the device on which it is running, such as a computer, could also compromise the software firewall.

Whereas a hardware firewall also has underlying software, typically that footprint is smaller (to provide less of a target for attackers) or specialized



## Host vs. appliance vs. virtual.
A host-based firewall is a software firewall that runs on and protects a single endpoint device (a host).
- All modern OSs include a host-based firewall.
- Topology independent — all (internal and external) attacks must go through the firewall
- Extensible — new servers can be added to the network, with their own firewall, without the need of altering the network configuration
- A closer look at the configuration settings reveals that these firewalls tend to be application-centric: users can create an opening in the firewall for each specific application.
- This approach is more secure than permanently opening a port in the firewall that always remains open as opposed to a port that is only opened when the application requires it and is then closed.
- An appliance firewall is typically a separate hardware device designed to protect an entire network
- A virtual firewall is one that runs in the cloud. Virtual firewalls are designed for settings, such as public cloud environments, in which deploying an appliance firewall would be difficult or even impossible.



# Firewalling Position (Architecture)
- Screening Router (typical packet filter)
- Dual-Homed gateway (Dual-Homed host)
- Screened host gateway
- Screened Subnet









f