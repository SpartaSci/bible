---
tags:
  - wireless
  - confidentiality
  - communication
  - DoS
---
[[wireless/WLAN/_wlan|_wlan]]

# DoS
> DoS is the act of **denying** a computer user of a particular service, typically by *flooding* a client with more traffic that it can handle


[[wireless/WLAN/WIFI|802.11]] is more vulnerable than 802.3 to DoS attacks because of the **shared medium**

**L1**: Radio Frequency Attacks or Jamming the wireless spectrum. The disruption occurs when SNR ratio reach a certain level

**L2**: Protocol-based attacking. The higher layer of communication by denying and media-access control services.

[[cybersec/attacks/SYN flood|SYN flood]]
[[cybersec/attacks/ping flooding|ping flooding]]


# identity vulnerability
802.11 nodes are **identified at MAC layer** by unique address.

The frames are **not authenticated**, an attacker change its MAC address and [[cybersec/attacks/spoofing|spoof]] other nodes, similarity to what it is done in [[cybersec/attacks/ARP spoofing|ARP spoofing]], since there is no signature,no confidentiality


## disassociation attack
a client can authenticate with multiple [[wireless/WLAN/WIFI#^1de188|APs]] but **associate** with one to allow the correct AP to forward packets. Associate frames are **NOT AUTHENTICATED**.
802.11 provides a *disassociation message* like the *deauthentication message*.

The vulnerability stands in **spoofing a message causing the AP to disassociate the client** 


## deauthentication attack
during the authentication procedure after selecting an AP for communication, the STAs must authenticate themselves to the AP with their MAC address. 
There is a specific message allowing clients to explicitly deauthenticate from the AP.

The vulnerability stands in the fact that an attack can [[cybersec/attacks/spoofing|spoof]] **the deauthentication message** causing the communication between AP and the legitimate client to suspend, hence, causing a DoS. The result is that the client **must re-authenticate** to resume communication with AP

Moreover, by repeating the deauthentication attack, the client can be kept from transmitting or receiving data **indefinitely**. Lastly, the attack can be executed on an **individual** client or on **all clients**:
- individual: attacker **spoof client's** address telling AP to deauthenticate the legitimate client
- all: attackers **spoofs AP** address telling all client to deauthenticate
[aircrack](http://aircrack-ng.org/doku.php?id=deauthentication)


> [!NOTE] Deauthentication vs Diassociation
> Deauthentication is more effective since requeires 2 RTTs (authN and associaiton) to resume communication, while disassociation only 1 RTT


### practical deauthentication defense

The **delay honoring deauthentication request** solution is based on the observed behavior that when legitimate nodes want to deauthenticate, they should stop sending data packets. Basically the honoring of the deauthentication request is delayed:
- delayed by small interval (5-10 seconds)
- if no other frames are received from source then **honor the request of deauthentication** 
- if source sends other frames then **discard the request of deauthentication**

### more robust defense

The starting idea is to create a *signature* to validate the client deauthentication request. SNR is defined as the sequence number, which is part of the *signature*. 
A possible signature could also be the noise: is the signal strength, therefore the [[signal analysis/SNR - Signal to Noise Ratio|SNR]] (signal to noise ratio) matching the client one?
1. First check signal strength
2. then check sequence number


# Attacks on CSMA-CD

[[wireless/WLAN/CSMA-CD|CSMA-CD]]

# Attack on CMSA-CA
[[wireless/WLAN/CSMA-CA#Attack on RTS/CTS virtual carrier sense|CSMA-CA]]

# Attacks on Power Saving in 802.11

[[wireless/WLAN/IEEE 802.11#power saving attacks|IEEE 802.11 power saving]]



# things not to do

**MAC authentication is useless**. Since MAC addresses are sent in cleartext and MAC addresses can be cloned (sniffing, spoofing,replay) 

**Static IP addresses are useless**. Cause IP addresses are sent in cleartext, they can be spoofed and it is easy to find and use a valid IP address

**SSID Hiding is useless**. [[wireless/WLAN/IEEE 802.11#^e1b824|Beacons]] can be suppressed, but the SSID is still sent in cleartext in the *probe request and response* and in the association response. Remember that in the authentication phase there is the information regarding the SSID.

**Smart antenna placement and hiding is useless**. As the attacker have infinite resource and use much more powerful device than yours


The only solution is **serious cryptography**

[[wireless/WLAN/Security/WEP - Wired Equivalent Privacy|WEP]] --> [[wireless/WLAN/Security/Chop Chop attack|Chop Chop attack]]

[[wireless/WLAN/Security/802.1x|802.1x]]
[[wireless/WLAN/Security/802.11i|802.11i]]   -> [[wireless/WLAN/Security/KRACK attack|KRACK attack]]



[[wireless/WLAN/Security/OWE - Opportunistic Wireless Encryption|OWE - Opportunistic Wireless Encryption]]

[[wireless/WLAN/Security/WP3|WP3]]
