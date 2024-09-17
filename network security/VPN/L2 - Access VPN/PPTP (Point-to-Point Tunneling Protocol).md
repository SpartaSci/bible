---
aliases:
  - PPTP
---
PPTP is a customer-provisioned solution with its own weak mechanisms for encryption and authentication. It was initially deployed and then adopted and modified by Microsoft.

As a *[[network security/VPN/_VPN#^bfee45|customer-provisioned]]* deployment mode, the customer (the host) creates the tunnel between itself and the VPN gateway of the corporate network (for which access is required). 

PPTP uses the MPPE algorithm for encryption and the MS-CHAP for authentication (both created/modified by Microsoft). Additionally, it uses the PNS (PPTP Network Server), which is the corporate (VPN) gateway, and the PAC (PPTP Access Concentrator), used only in provider-provisioned deployment mode. Finally, it employs double tunneling (PPP tunneling and then GRE for tunneling of PPP over IP) for the PPTP Data Tunneling and requires a Control Connection that uses TCP encapsulation for managing the data tunnel setup, management, and teardown.