---
tags:
  - encryption
  - confidentiality
  - wireless
  - communication
aliases:
  - WEP
---

# WEP goals

**Reasonably strong**: length of secret key and frequency of changing bits properties need to be relatively strong against **brute-force** attacks-
In this sense, WEP avoids brute force by **frequently changing IV** and the key K

**Self-Synchronizing**: Provided by the IV, which is sent in cleartext, to let the receiver self-synchronize with the same IV and hence compute the same key K. Bare in mind that it is a **best effort** delivery approach and **packet loss** rates can be high

**Efficient**: WEP algorithm is very **efficient** in comparison to traditional block ciphers, as it uses few resources and can be implemented efficiently in HW or SW

**IP content**: WEP proposal is Intellectual Property free. No royalty to pay


# Access control
Two different authentication methods can be used with WEP: 
- **open system authentication**, which means no password
- **shared system authentication**, shared reusable password

Access control an **STA to be authenticated by the AP before the association**

The authentication process is based on a simple *symmetric challenge-response*:
- STA knows key $k$. It sends an *Authentication request* to the AP
- AP also knows key $k$. AP send a challenge $r$ 128 bits longs. The key is not used to encrypt but to start the [[crypto/symmetric/stream/RC4|RC4]] keystream generation. The result byte sequence $K_{rc4}$ is xored to the challenge $r$, resulting in $E_k(r)$ encrypted response to the challenge.

Anybody can authenticate themselves without knowing the real key, as the attacker can sniff the challenge $r$ and the encrypted response $E_k(r)$. Therefore, in order to retrieve the key $k$ the only operation to perform is the reverse XOR: $$r \ xor \ E_k(r) = K_{rc4}$$

> [!Attention] Shared key auth is not more secure than Open system auth
With a brute force approach an attacker can retrieve the $k$ from the keystream, and since is the same used for confidentiality he has access to all messages


# Integrity and Confidentiality
WEP utilizes **Cyclic Redundancy Check** CRC-32 checksum to provide data integrity to WLAN transmission.

**ICV** (integrity check value) added to each frame, by using the simple CRC32 algorithm

WEP confidentiality is provided by **encrypting**  the message before the transmission. The algorithm used is the [[crypto/symmetric/stream/RC4|RC4]] algorithm, same one for authentication

First we attach CRC to the payload, then we encrypt all. (authentication then encryption)

# RC4 in WEP

Is essential that each message is encrypted with different key stream, so $k$ is the same (**shared secret**), but a different 24-bit IV for every message

For each message:
1. RC4 produces a pseudo-random byte sequence $K_{rc4}$
	- initialized by the $k$ and an $IV$
2. This pseudo-random sequence is xored to the message

remember IV is sent in clear


# key management

**Default key**, also called shared key, group key, multicast key

**Key Mapping Keys**, also called individual key

In practice, only default keys are supported and used, therefore, each STA **uses the same shared *secret* key**, implying that every STA can decrypt any other STA messages.

The **default key** is a group key, and a group keys need to be changed when a member leaves the group. It is practically impossible to change the default key in every device simultaneously, therefore, **WEP supports multiple default keys** to help smooth change of key.

The message header contains a key ID that allow the receiver to find out which key should be used.



# Flaws
## authentication and access control

Access control:
- authentication is one-way 
- AP is **not authenticated** to STA
- STA is at risk to associate with a **rogue AP**

Shared system authentication -> leak the key -> see before
Open system authentication -> no access control at all

Same shared key for both authentication and encryption

## integrity and replay
There is no replay protection at all, since the IV is not mandated to increment after each message..

Problems in WEP integrity: possible **collision** due to simplicity of 
CRC-32
Moreover the attacker can manipulate messages despite the ICV mechanism and encryption since CRC is **linear function** with respect to XOR: 
$$CRC(x \ XOR \ y) = CRC(x) \ XOR \ CRC(y)$$

Therefore if an attacker modifies the message, he can compute the CRC of the modified message, and then XOR it with the initial valid CRC. This is equivalent to both modifying the payload and the CRC **without knowing the K**

## confidentiality and IV

IV reuse, IV is long 24 bits, after $2^{24}$ messages to encrypt, a previously used IV will be re-encountered, allow to build a decryption table for statistical attacks

**Weak shared key**: for some seed values, called weak key, the beginning of the RC4 output is not random, therefore, the first few bytes of the output reveals a lot of information about the key.

[[wireless/WLAN - wifi/Security/Chop Chop attack|Chop Chop attack]]

