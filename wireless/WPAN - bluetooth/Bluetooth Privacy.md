
[[wireless/WPAN - bluetooth/bluetooth security|bluetooth security]]

Bluetooth devices continuously send data in packets containing the MAC address of the sender and receiver, making it possible for an attacker to passively listen to packets and track a device person

**Solution**: To mitigate, changing the MAC address frequently is recommended.

In practise, using **private addresses** that are **randomly generated** and rotated frequently. Ideally every 15 minutes

Paired devices can maintain their pairing by using **resolvable private addresses** generated using the device **Identity Resolving Key IRK** generated during boinding

**Device Privacy Mode**: only concerned about its **own privacy**

**Network Privacy Mode**: it shall not accept advertising packets containing Identify Address of peer devices that have not distributed their IRK

# device addresses

**public address**: global and fixed

**random address**: not registered

**static address**: randomly generated at each boot

**private address**: generated and rotated to avoid tracking


