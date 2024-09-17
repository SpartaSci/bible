

# VPN gateway positioning

Now, where should we position a VPN Gateway?

**Inside**: it implies no inspection of VPN traffic (by the firewall because the firewall can also pass through the traffic to the gateway) and that the VPN gateway is protected by the firewall because it is inside the network.

**Outside**: it implies that the VPN gateway is protected by access router (weak) but the content of traffic can be analyzed by the firewall because it is decrypted before arriving to the firewall that is the next hop after the VPN gateway when it is put outside the internal network.

**Integrated**: it allows to reach maximum flexibility.

**Parallel**: it can lead to potential uncontrolled access.

An other problem of the VPN gateways is the use of [[network/NAT - Network address translation|NAT]] because the NAT can change the addresses (the checksum will fail and so on) and so on. For this and other reasons, the NAT should be put before the gateway.


Ideologically correct order should be: NAT → Firewall → VPN Gateway → Firewall. In this way, the traffic can be analyzed in any case and the gateway is protected as well. Typically, also the [[network security/Monitoring/IDS - Intrusion Detection System|IDS]] is usually outside the firewall.


Moreover, there can be different anomalies that can occur. We analyzed two anomalies, both belonging to anomalies related to insecure communications.

**Monitorability anomaly**: it is when some nodes at the channel junctions can see the exchanged data.

**Skewed channel**: it is when a wrong tunnel overlapping removes the confidentiality in a part of the communication.