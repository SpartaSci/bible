


- **BT classic**:
	- (v1.1) [[wireless/WPAN - bluetooth/security/pairing/Legacy Pairing|Legacy Pairing]]
	- (v2.1) [[wireless/WPAN - bluetooth/security/pairing/secure simple pairing|secure simple pairing]]
	- (v4.2) [[wireless/WPAN - bluetooth/security/pairing/BR Secure connection|BR Secure connection]]
- **BLE**:
	- (v4.0) [[wireless/WPAN - bluetooth/security/pairing/BLE Legacy Pairing|BLE Legacy Pairing]]
	- (v4.2) [[wireless/WPAN - bluetooth/security/pairing/BLE secure connections|BLE secure connections]]



Four association models, to create a **Temporary key**
- **Just Works**
- **Numeric Comparison**: (6-digit PIN) User compares the numbers displayed and confirms both are same. 
- **Passkey Entry**: User reads 6-digit pass-code from A and Enters the value in B. (OR) User enters same 6-digit pass-code in both A and B
- **Out-Of-Band**: Different Wireless protocol (e.g NFC) is used to authenticate the communication.





# pairing Steps

1. **pairing feature exchange**: in this phase the initiator and the responder will negotiate over which [[wireless/WPAN - bluetooth/security/security modes and levels|security modes and security levels]] to choose
2. key for encryption
	1. **LE legacy pairing**: short term key **STK** 
	2. **LE Secure Connections**: long term key **LTK**
3. **Transport specific key distribution**



**STK (Short Term Key)**: used as the key for encrypting a connection the very first time two devices pair. The STK is generated using 3 pieces
of information:
- The **TK** is used as the key for the encryption engine
- Srand random number contributed by the slave
- Mrand random number contributed by the master
$$STK = E_{tk}(Srand | Mrand)$$
 Used only for pairing and **LTK** key distribution

# bonding

**Bonding**: store keys to avoid pairing each time

**LTK (Long Term Key)**: distributed once the initial pairing procedure has encrypted the connection 
- A random number stored in a security DB
- Generated on the slave device