---
aliases:
  - L2TP
---
L2TP uses [[network security/VPN/L3 - IPsec/_IPsec|_IPsec]] to achieve security and is independent of the Layer 2 protocol on the host. It is considered a *provider-provisioned* solution that allows tunneling between the public network access point (access provider) and the corporate network (Internet Service Provider).

L2TP employs an LAC (L2TP Access Concentrator), typically the NAS (Network Access Server), which supports L2TP and performs the necessary operations, and an LNS (L2TP Network Server), which is a corporate (VPN) gateway. The host connects via a PPP connection to the LAC. Within the L2TP session, the LAC performs tunneling operations and forwards the traffic to the LNS, which decapsulates it and acts as a pass-through for the traffic.