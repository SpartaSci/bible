---
tags:
  - authentication
aliases:
  - EAP
---
# EAP

> carrier protocol designed to transport the messages of real authentication protocols (e.g. TLS)

[[wireless/WLAN/Security/802.1x|802.1x]]

Four type of messages:
- **EAP request** - carrier messages from the *supplicant* to the *authentication server*
- **EAP response** - carrier messages from the *authentication server* to the *supplicant*
- **EAP success** - signal successful authentication
- **EAP failure** - signals authentication failure


# EAPOL - EAP over LAN 
[[wireless/WLAN/Security/802.1x|802.1x]]
Encapsulate EAP messages into LAN protocols (e.g. ethernet)

EAPOL is used to carry EAP messages between the [[wireless/WLAN/WIFI|STA]] and the [[wireless/WLAN/WIFI|AP]]

# RADIUS

Carrier EAP messages between the AP and the *authentication server* 

MSMPPERECV key attribute is used to transport the **session key** from the *authentication server* to the AP (*authenticator*)
