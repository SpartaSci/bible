
**Bluetooth security services** include: 
- [[cybersec/_properties/authentication|authentication]]: is to verify the identity of communicating device. User authentication is not provided natively by Bluetooth
- [[cybersec/_properties/authorization|authorization]]: allows the control of resources. A bluetooth device must be authorized to use a service
- [[cybersec/_properties/confidentiality|confidentiality]]: user data is encrypted before transmission

**Features**:
- **pairing**: the process of creating one or more shared secret keys
- **bonding**: storing the keys created during pairing
- **device authentication**: verification that the 2 devices have the same keys
- **encryption**
- **message integrity**


# BT vs BLE
## BT classic 


Secure simple pairing (before 4.2)

Secure connection (after 4.2)

## BLE
In BLE inside the SMP (security manager protocol)
- peer to peer protocol used to generate and stores encryption keys and identity keys
- generates **random addresses** every 15 minutes

LE Legacy security use AES-CCM encryption
New -> **Secure connection** -> improve LE legacy


# modes and levels

**level 1**: no security

**level 2**: *unauthenticated pairing with encryption*

**level 3**: *authenticated pairing with encryption*

**level 4**: *authenticated Low Energy Secure connections pairing with encryption using a 128 bit strength encryption key*

**mode 1**: levels *without signing data*

**mode 2**: levels *with signing data*

**mode 3**: deals with security data in broadcast communication


# pairing Steps

1. **pairing feature exchange**: in this phase the initiator and the responder will negotiate over which security modes and security levels to choose
2. key for encryption
	1. **LE legacy pairing**: short term key **STK** 
	2. **LE Secure Connections**: long term key **LTK**
3. **Transport specific key distribution**

# Secure simple pairing
The primary goal is to **simplify the pairing procedure** for the user. 
The secondary goals are to **maintain and improve the security**
Protect against [[cybersec/attacks/sniffing|eavesdropping]] and [[cybersec/attacks/MITM|MITM]]


# aaa da finire tanta merda

[[wireless/WPAN - bluetooth/Bluetooth Privacy|Bluetooth Privacy]]
[[wireless/bluetooth/Bluetooth confidentiality|Bluetooth confidentiality]]

