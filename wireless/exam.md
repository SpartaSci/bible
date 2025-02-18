# GNSS


### gnss segments
Which three system segments comprise a GNSS? Briefly describe their role and characteristics as part
of the overall system.
1. Identify the three segments that make up a GNSS. (2 points)
2. Briefly describe the role, characteristics, and challenges of each GNSS segment. (3 points)
3. How do theese segments interact to ensure the system’s overall accuracy, reliability, and functionality? (1 point)

**solution**
The three segments that compose a GNSS system are: space segment, control segment and user segment.

**Space segment**: is composed by a constellation of satellites that keep broadcasting navigation signals in different frequencies in L band. These signals contain spreading code and navigation data (position and transmission timestamp) that allow the receiver to computate their PVT. Satellites must send be synchronized. 

**Control segment**: a network of station distributed around the earth in order to monitor the status of the satellites and signals, ensuring the overall synchronization. Is composed by a tracking station that collect the data, a master station that process the data and a uploading station that send the data to the satellites.

**User segment**: are different receivers, with difference performance level, that use multiple signals from different satellites to estimate the position of the user. Common steps are identification of the satellite, computation of the pseudorange, estimation of PVT. 

The Control segment interact with the Space segment to adjust the time synchronization. The Space interact (unidirectional) with the User. 
The control and user segment don't interact.



### gnss broadcst information
In a GNSS, satellites broadcast crucial information to the users:
1. Identify the crucial pieces of information that satellites broadcast to users. (2 points)
	- List the essential data elements transmitted by GNSS satellites to receivers.
2. Explain how these pieces of information are utilized by a receiver. (4 points)
	- Describe how the receiver utilizes satellite signals to calculate its position, velocity, and time (PVT).

**solution**
The GNSS is a broadcast one way wireless system, where satellites send continuous signal to the earth without receiving back. 

Satellites sends 2 important information: **orbital data** (its position) and the **transmission timestamp**, that thanks to atomic clock on satellites and correction from control segment, we can consider correct and with zero bias.

The receiver using T_tx (transmission time), T_rx (receiving time) and C (speed of light) can compute the geometrical range R = (T_tx-T-rx)\*C 
Intuitive, with 3 satellites and 3 ranges, we can image 3 sphere (satellite as origin and range as radius) , we can image the user position as the intersection of these sphere (two intersection but only one on earth). 
Practically we have to consider also the receiver bias (dTu) that cannot be corrected as the satellite once. 
So we have to find (x_u, y_u, z_u, dTu) and we need at least 4 satellites to resolve the estimation problem.
It consist in solve the system of equation (pseudorange eqaution) where:
p1 = sqrt\[ (x1 - xu)^2 + (y1-yu)^2 + (z1-zu)^2 \] + b_ut
p2 = ..
p3 = ..
p4 = ..

(xj, yj, zj) satellite position (known)
pj = pseudorange = radius of the pseudo sphere (known)
(xu,yu,zu) user position  (unknown)
b_ut = dTu*c  user clock bias (unkown) 

It is a non-linear estimation problem that can be linearized thorough Taylor expansion and than solves using Least square solution. 


### pseudoranges error
Describe the effect of pseudorange errors on the Position, Velocity, and Time (PVT) solution and explain the role of the Dilution of Precision factor (e.g., GDOP, HDOP).

1. Explain the effect of pseudorange errors on the Position, Velocity, and Time (PVT) solution. (3 points)
	- Describe how errors in the measurement of pseudoranges from GNSS satellites affect the accuracy of the PVT solution.
2. Discuss the role of the Dilution of Precision (DOP) factor in GNSS positioning. (3 points)
	- Define what Dilution of Precision (DOP) factors (e.g., GDOP, HDOP) represent in GNSS.
	- Discuss the relationship between DOP values and the accuracy and reliability of the PVT solution.
	- Provide examples of scenarios where high and low DOP values impact GNSS performance.

**solution**

Pseudorange errors affect the accuracy of position, velocity, and time (PVT) in GNSS. These errors can result from atmospheric conditions (ionospheric and tropospheric delays), satellite clock errors, and signal propagation issues (multipath and interference), leading to inaccuracies in the computed PVT solution.

Dilution of Precision (DOP) quantifies the impact of satellite geometry on positioning accuracy. A well-distributed satellite configuration reduces DOP, improving accuracy, while poor geometry increases DOP, leading to greater errors. GDOP affects overall PVT accuracy, while HDOP specifically influences horizontal positioning.

For example, the environment can limits which satellites reach us so, low DOP values in open-sky environments improve GNSS accuracy, whereas high DOP in urban canyons or obstructed areas degrades performance.


# gnss attacks

### interference detection methods

Interference detection methods can vary in their approaches within GNSS receivers:
1. List some interference detection methods used in GNSS receivers. (2 points)
	- Identify at least two different methods used for interference detection.
2. Briefly describe each interference detection method. (4 points)
	- Provide a concise explanation of how each method detects interference within GNSS receivers.
	- Discuss the advantages or limitations of each method (e.g., in terms of effectiveness and implementation complexity).

**solution**
- **AGC Dynamic Observation**: this method uses automatic gain control (agc) adaptation employed by the receiver. By observing the AGC's variation over time, we can identify high-power interferences over the GNSS band, which can be used to detect attacks like spoofing. When high-power interference signals are processed by the receiver, the AGC lowers the input gain on the RX chain, causing a sudden shift in the AGC graph. These sudden variations can be used to detect interference. The advantage of this method is that it can also be used for spoofing detection and only require the enablement of AGC measurement for the RX chain.
- **SNR Measurements**: high variations in the Signal-to-Noise Ratio SNR can be used to detect interference signals that affect the overall signal quality and are directly measured by the receiver. High spectral noise will degrade signal performance, causing a change in the SNR. This method is moderately accurate and fast.
- **Machine learning models**: other methods involve feeding data into machine learning models that can be trained on normal scenario. These models can later be used for detection. This method is generally precise (depending on the model used and the amount of training data) but will require more power and data for inteerference.
- **Goodness-of-Fit**
- **Spectral analysis**



### jamming vs spoofing

3. What are the main differences between a spoofing and a jamming attack on a GNSS receiver?
	1. (2 points) Define what constitutes a spoofing attack and a jamming attack.
	2. (2 points) Compare and contrast the mechanisms by which each attack operates. Discuss how each type of attack impacts the GNSS signals. Highlight the differences in the effects on the receiver’s position, velocity, and time (PVT) calculations.
4. (1 point) Which type of attack is more harmful to GNSS operations?
5. (1 point) Explain your reasoning for which attack is more harmful.

**solution**
A **jamming** attack consist of the denial of navigation signal service (DoS attack) by hiding the navigation signals under noise. In the case of a jamming attack the victim will not be able to estimate its position correctly. Mass market jammers usually aims at disturbing wide range of frequencies by modulating a pure tone. 
**Spoofing attack** involves sending fraudulent GNSS-like signals to the receiver, causing it to calculate a wrong estimated position. The aim of the attacker is to take control of the receiver device by making it estimate an incorrect position. The spoofed signal must meet certain constraints to be accepted by the receiver, it must have a similar pseudo-random noise pattern to a real GNSS signal, be compatible with the GNSS time scale, have a similar direction of arrival, and exhibit similar power and Doppler effect characteristics

The most harmful is the spoofing attack, as the victim is fooled without any notice. PVT calculations are fundamental for economic transactions and legal purpose. In contrast, jamming can be immediately recognize by impossibility to compute the PVT.

### meaconing (spoofing)
Based on the explanations provided in class and your laboratory experiences, please address the following:
6. (3 points) Describe a meaconing attack on a GNSS receiver. Define what a meaconing attack is. Explain how it is conducted. Mention any distinguishing characteristics of a meaconing attack compared to other types of GNSS interference.
7. (3 points) Discuss the effects of a meaconing attack on a GNSS receiver. Describe the impact on the receiver’s position, velocity, and time (PVT) calculations. Highlight any possible indicators that a meaconing attack is occurring.

**solution**


In a GNSS system, a **meaconing attack** is performed by rebroadcasting (toward the victim receiver) after some time delay previously captured legitimate satellite messages. Due to the design of GNSS system, such kind of messages can lead the receiver to estimate wrong PVT.
Receiver terminals indeed rely on the measured time difference between transmission time (contained in the signal) and reception time. When old satellite messages are received, the time measured is inevitably wrong. PVT calculation are going to be less accurate, usually observable by sudden jumps in the computed position.

Rebroadcasting all captured satellite signals after a fixed time delay is probably not going to affect much the PVT calculations on target victims, as the fixed time delay is going to be compensated by the user clock bias variable (used to handle clock desynchronization between user devices and satellites system)

Compared to other types of GNSS interference, like jamming, the goal is not completely deny the GNSS service to the victim, but to make the computed position unreliable. 

Meaconing attack can be detected after the computation of PVT, by sudden jumps in computed position, and at physical layer, like for jamming and spoofing, by different signal strength, noise, ans SNR levels compared to the legitimate signals received by satellites.



### interference detection and mitigation domain
Describe interference detection and mitigation approaches based on transformed domains adopted in GNSS receivers. (6 points)
1. (3 points) Explain the general interference detection and mitigation approach based on transformed domains used in GNSS receivers.
	- Discuss how transformed domains (e.g., frequency, time-frequency) are utilized to detect and mitigate interference.
	- Provide examples of specific techniques or algorithms used in transformed domains for interference detection and mitigation
2. (1.5 points) List and describe a frequency domain mitigation technique.
	- Identify a specific technique used in the frequency domain for mitigating interference in GNSS receivers.
	- Describe how this technique operates to suppress or filter out interference signals effectively.
3. (1.5 points) List and describe a time domain mitigation technique.
	- Identify a specific technique used in the time domain for mitigating interference in GNSS receivers.
	- Explain how this technique analyzes temporal characteristics of signals to detect and mitigate interference.


**solution**
Interference detection and mitigation in GNSS receivers leverage transformed domains to separate GNSS signals from interference. The general approach consist of:
- **transformation** of the received signal in a different domain (e.g. frequency, time-frequency) where interference is more distinguishable
- applying thresholding, statistical methods, or machine learning to **detect** anomalies
- interference suppression or cancellation 
Example of techniques are a Fourier transformation, or more advances Gabor transformation, Wavelet Packet Decomposition, Karhunen-loeve Transform 

A frequency domain mitigation technique is **Notch filtering**.
Detects interference in the frequency spectrum and applies a narrowband filter to remove specific unwanted frequencies. Help mitigate continuous wave jammers or narrowband interference. The adaptive version can be used against swept frequency jammers.
Need a precise estimation of the interference frequency.

A time domain mitigation technique is **Digital Pulse Blanking**. We monitor the amplitude of the received signal and blank high-pulses exceeding a predefined threshold.  
Can also blank useful GNSS signal causing noise

### spoofing attack
What are the effects of a spoofing attack on a GNSS receiver? Motivate your answer. (6 points)
1. (3 points) Describe the primary effects of a spoofing attack on a GNSS receiver’s operation. Explain how spoofing can alter the receiver’s position, velocity, and time (PVT) calculations. Discuss potential disruptions in navigation and timing accuracy.
2. (3 points) Provide a detailed explanation to support your answer. Discuss how the GNSS receiver might respond or fail to respond to spoofed signals. Explain why these effects occur, considering the technical aspects of GNSS signal processing.

**solution**

**Spoofing attack** involves sending fraudulent GNSS-like signals to the receiver, causing it to calculate a wrong estimated position. The aim of the attacker is to take control of the receiver device by making it estimate an incorrect position. The spoofed signal must meet certain constraints to be accepted by the receiver, it must have a similar pseudo-random noise pattern to a real GNSS signal, be compatible with the GNSS time scale, have a similar direction of arrival, and exhibit similar power and Doppler effect characteristics.


### spoofing countermeasures

1. List and describe some possible spoofing countermeasures for satellite navigation systems. (3 points)
	- Identify at least three spoofing countermeasures.
	- Briefly describe how each countermeasure works.
	- Explain the effectiveness of each countermeasure in mitigating spoofing attacks.
2. Specify the levels of a satellite navigation system at which these countermeasures can be implemented. (3 points)
	- Identify the different levels within a satellite navigation system.
	- For each of the countermeasures mentioned above, indicate the level(s) at which they can be applied.

**Direction of Arrival analysis**: GNSS signals originate from known satellite positions. A receiver equipped with multiple antenna can estimate the direction of arrival, and if it is inconsistent the signal may be considered spoofed. High effective against single-source spoofing, not effective against sophisticated attacker that can mimic legitimate satellite geometry. It can be implemented ad Antenna level (user segment)

**Authentication**: Satellites send encrypt or digitally signed data.
It is very effective, but can not prevent meaconing.
It is implemented in Space segment

A general technique for interference detection is look for some inconsistency in synchronisation to GNSS timescale, in the navigation message, power level, cross check with other pseudoranges, or integrating other measures of other sensors.
This is applied a receiver level



# WLAN (no wep wap)



### goodput calculation

Consider a setup in which 2 STA (STA-1 and STA-2) are connected to the same WLAN managed by an AP. A third device (ETH-1) is connected with Ethernet technology. For each setup, describe and justify the expected goodput in the following cases:

data: 
1. both STA use 802.11g on ISM band, Fast ethernet, so 100Mbps
2. STA1 use 5GHz
3. both 802.1ax (wifi 6), STA1 on 5Ghz, STA2 on 2.4Ghz

Data to remember 
ISM -> 2.4GHz
**802.11g -> 54Mbps**
Fast ethernet -> 100Mbps

use 5GHz -> 802.11n -> 600Mbps

802.11ax -> in other exercise give also maxx bit 1.1Gbps and eff 80%

**solution**
eff UDP ETH = 1500 - 20 (ip) - 8 (UDP) /  1500 + 38 = 0.9..
eff TCP ETH = ...
**eff 802.11g -> TCP 0.50, UDP 0.55**

procedure: find bottleneck, calculate expected goodput (eff per bitrate)

if both STA are involved with 802.11g 2.4, channel is shared so /2
if STAs uses different channel no problem 




### 802.11 power management capabilities and attack

Describe the 802.11 power management capabilities (4 points)
- How can an STA tell the AP that it is going to sleep?
- For how long would the AP not be able to transmit frames to a sleeping STA?
- How can the AP tell the STA that it has some buffered frames waiting to be sent?

Describe with an example the sequence of frames exchanged over a time between the STA and the AP.
You can use a numbered list and state who sends what to who, or which computations a device does with some information:
1. STA sends frame XXX to AP
2. AP sends frame YYY to broadcast
3. STA extracts ZZZ from YYY and computes KKK, YYY, LLL
4. ...
How can an attacker abuse of these mechanisms to mount a DoS attacks? (2 points)

**solution**
The power management capabilities allows the device to go to sleep in order to conserve energy. 
When a STA wants to go to sleep, it send a dummy packet to the AP with the power management flag set to 1. During the time, if the AP has to transmit some packets to the STA, it will start buffering the. The STA will wake up before the next beacon frame from the AP (which are send periodically, so synchronization is important). If the AP has buffered some packets, it will notify the STA of those packets via the TIM field in the beacon. Based on the TIM value, the STA will wake up to receive the buffered packets or will go back to sleep if the AP does not have any frames to send. 

Sequence of frames:
1. STA send a null frame with power management flag set to 1
2. AP send ACK and STA go to sleep
3. AP sends the periodic beacon with the TIM field set
4. The STA analyzes the TIM value:
	- if the AP does not have any packets buffered for the STA, the STA goes back to sleep until the next beacon
	- if the AP has some packets buffered, the STA will wake up
5. STA send a poll message to request the buffered packets.
6. Transmission of buffered frames from AP to STA
7. STA send ACK

The power management mechanism ca be used to mount a DoS attack in different ways:
- the attacker inject some false synchronization frames to cause the STA and the AP to fall out of synchronization. As a result the STA will not wake up in time for the beacon and will not be able to correctly receive the frames
- the attacker impersonates the STA, and keeps injecting false power management frames with the bit set to 1. Therefore, the AP will think that the STA is sleeping and start buffering packets. The AP sends a beacon frame with TIM to signal the victim to wake up, but the victim will ignore the TIM since is not in power management




### auth assos open system
Describe and sketch the sequences of messages a STA and an AP exchange during the initial Association
and Authentication process in an Open System.
Consider both the case in which
• The AP broacasts the beacon messages (2 points)
• The ESSID is hidden and the AP does not broadcast the WLAN ESSIS in the beacons (2 points)
What type of attacks such mechanisms allow? (2 points)
To describe the timeline, you can use a numbered list and state who sends what to who, or which
computations a device does with some information:
1. STA sends frame XXX to AP
2. AP sends frame YYY to broadcast
3. STA extracts ZZZ from YYY and computes KKK, YYY, LLL
4. ...

**solution**
Case 1
1. The AP sends the beacon frame in broadcast to inform all the STAs that there’s an AP with the name expressed in the frame.
2. The STA interested in connecting to that AP replies with a probe request.
3. The AP replies with a probe reply.
4. STA sends an authentication request
5. STA sends an association request to the AP.
6. AP replies with an association reply.

Case 2:
1. STA can send a probe request in broadcast to discover which APs are present in the network.
2. Only the APs that accept broadcast requests send a probe reply, indicating the corresponding ESSID.
3. All the points from 3 to 5 are the same as in Case 1

These mechanisms allow two types of attacks. Exploiting the authentication and association vulnerabilities (lack of sender authentication), the attacker can send, on behalf of the AP, a broadcast (or directly to a STA) **disassociation or deauthentication frame**. This implies that all the STAs connected to that AP will perform the association or authentication mechanism again. The most effective one (from the attacker’s point of view) is the deauthentication attack since it forces the STAs to perform both association and authentication procedures again, requiring more time before the STAs reconnect to the AP.


### SAE (Simultaneous Authentication of Equals)
- Discuss the concept of SAE (Simultaneous Authentication of Equals) in WPA3 (3 points) 
- How does SAE improve the authentication process, and what are its advantages over the PSK (Pre-Shared Key) method used in WPA2? (3 points)

**solution**
SAE is the major feature introduced in WPA3. It provide more robust password based authentication. SAE replaces the 4-way handshake used in WPA2, begin robust against KRACK attack. 
It is based on Elliptic curve Diffie Hellman. 

The password is used with diffie hellman to authenticate both parties.

And for the message flow, the encryption, is generated a new PTK at each connection, so the disclosure of one does not affect other session givin Perfect forward security. Also the disclosure of the PSK is not a problem since is used only for the authentication.



### brute force WPA-personal
Describe a possible brute force attack to a WPA-personal setup (3 points)
Explain how WPA3 enhances protection against offline dictionary attacks. What specific features of WPA3 contribute to this improved
security? (3 points) 
Show the sequences of messages two stations exchange to complete the initial mutual authentication in WP3 using the Simultaneous Authentication of Equals (SAE) protocol. To describe the timeline, you can use a numbered list and state who sends what to who, or which computations a device does with some information:

1. STA sends frame XXX to AP
2. AP sends frama YYY to broadcast
3. STA extracts ZZZ from YYY and computes KKK, YYY, LLL
4. ...




### KRACK

Describe the **KRACK attack** that targets the **four-way handshake** in the authentication phase. Show the sequence of messages in which the attack may be possible. To describe the timeline, you can use a numbered list and state who sends what to who, or which computations a device does with some information:

1. STA sends frame XXX to AP
2. AP sends frama YYY to broadcast
3. STA extracts ZZZ from YYY and computes KKK, YYY, LLL
4. ...

**solution**

Considering the 4 way handshake:
1. AP generates and send Anonce
	- Suppliant receive Anonce, generates Snonce, and generate PTK, calculate MIC 
2. Suppliant send Snonce and MIC
	- AP receive Snonce, generate PTK, calculate MIC, if is the same means they share PMK
3. AP send Key Installation Request, MIC, GTK
	- Supp calculate MIC and check it 
	- Supp install PTK and GTK
4. Supp send ACK+MIC

Now, the KRACK attack aims to block the message 4, so the AP will resend the message 3. Each time the client receive message 3, it reinstall the same session key, but with an incremental Packet Number and replay counter, a nonce used in encryption.  




# bluetooth


### bluetooth device states

Describe the Bluetooth device states (standby, advertiser, scanner, initiator, master, slave). (3 points)

Provide an example considering two devices that would like to interconnect. (3 points) 
You can use a numbered list and state who sends what to who, or which computations a device does with some information:
• A sends frame XXX to B
• B sends frame YYY to broadcast
• A extracts ZZZ from YYY and computes KKK, YYY, LLL
• ...


**solution**

Devices can be in six different states:
1. standby: initial state of all devices that are not actively communication
2. advertiser: a standby device move to this state and start sending messages to inform that it is a connectable devices, messages contain address and other info
3. scanner: a standby device move to this state and start receiving advertisement
4. Initiator: a scanner that has decided the advertiser to connect with, start the device discovery process, sends a scan request waiting for the response. It must specify the peer device address to which connect.
5. Master: after the connection is established initiator became the Master. It is now in charge of controlling all connections parameters and managing channel usage
6. Slave: the scanner move to Slave state

Standby -> advertiser --------- -> slave
standby -> scanner -> initiator -> master
After the connection is set up, the pairing procedure can start, allowing the devices to authneticate and exchange symmetric keys (according to security level) to be used to protect subsequent future connections.



### gatt
Explain the role of the Generic Attribute Profile (GATT) in Bluetooth Low Energy (BLE) technology.

How does GATT facilitate communication between devices, and what are its main components and operations? Discuss the practical applications of GATT in modern Bluetooth-enabled devices for some use cases.

**Solution**

The GATT is essential in BLE technology, defining how data is structured and exchanged between devices. 
It follows a client-server architecture where:
GATT client initiates communication by sending requests
GATT server receive them and respond

GATT facilitate communication organizing data as database:
- service, a collection of data and associated behaviours used to accomplish a particular feature
- characteristic, contains the value used in a service
- descriptor, description of the associated characteristic

An example can be a smartband that as service offer various characteristics like heart rate, body measurement


### design and physical layer
Explain the main design goals for the Bluetooth technology and the technical constraints that guided the design, and the Bluetooth network topologies and the role of nodes in each scenario. (2 points) 

Describe the physical layer communication mechanisms implemented in Bluetooth BR/EDR and the differences since BLE was introduced: 
- which frequency range does it use, 
- which multiple access scheme does it use, 
- which FEC/ARQ mechanism it provides, 
- etc. (4 points)

**solution**
*main goal*
The main goal for Bluetooth was to create a wireless cable rather than a wireless network. It is designed to be short range, low power and inexpensive

*topologies*
In the bluetooth protocol, we always have a master device and a slave device, forming a piconet. There can be maximum 7 slave for a single master. A master cannot be master in two piconet, but can be a slave in other piconet and be a link between the two piconet, also a slave can be a slave in more than a piconet. Slaves cannot comunicate directly between them. Master controls everything, communication prameters, which slave can communicate

*physical layer FHSS* 
The physical layer communication mechanism is implemented using FHSS which involves diving the channel into smaller channels and using a pattern (pre specified) to jump from one channel to another. This complicate sniffing attacks. A special version is Adaptive FHSS, where devices use statistical algorithm to choose channels based on the least busy one. If all devices use this mode, they will hop to the same channels making things worse.

*frequency band*
The frequency band used for both BR/EDR and BLE ranges from 2.4GHz to 2.485GHz, which is typically very busy. But BR/EDR uses 79 channels, hopping every 1600ms, while BLE use 40 channel, 37 reserved for data.

[[wireless/Communications/ARQ - automatic repeat request|ARQ]] uses ACK and NACK messages to ensure the correct reception of messages

[[wireless/Communications/FEC - forward error correction|FEC]] directly influences efficiency and can be implemented in two ways:
- 1/3 efficiency, where each message is sent over channel 3 times
- 2/3 efficiency, where for every 10 bits of data, 5 bits of error correction codes are sent, capable of correcting 1-bit errors and detecting 2-bit errors




### bluetooth privacy features
Which are the privacy features offered by Bluetooth? Which attack do they offer protection to? 
How is the problem solved using the **IRK**? Describe in detail how the IRK is used to provide resolvable private addresses.


**solution**

*The problem*
Bluetooth technology is mostly used for communication between personal devices like headphones or smartwatches. Device that presene indicate also the presence of the owner. In BT technology, devices sends periodically information and beacons, so an attacker can sniff the MAC address and with it can violate the privacy of the user. 
*The solution*
For this scope, is being added a **private resolvable address**.
Such address is computed from a random value with a key. Verifying the key is equally to verify the user. 

There are different types of address: public, random static, random private, resolvable or not resolvable. Each identified by 2 starting bits. 

The Identity Resolving Key IRK is exchanged during bonding phase

The resolvable address is composed by: 
24 bit hash of IRK and a 22bit PRAND random sequence
22 bit PRAND
2 bit 10 to identify the type (resolvable)

To verify the address:
extract the 22 bit PRAND
compute the 24 bit hash(IRK,PRAND)
check if is the same of the address



### association modes

Describe the Bluetooth association models and the mechanisms implemented to support the different capabilities a device could have. (3 points)

What is the goal of implementing such association models? (1 point)

What are the minimum hardware capabilities two devices must have to support each of the four association models? (2 points)


**solution**

In bluetooth, the four association models are based on different key agreement protocols, which are then used to encrypt the connection between devices. During the pairing process, hardware capabilities are exchanged to determinate the most secure association method supported by both devices.

The goal of implementing these association models is to offer different models that can be used based on the hardware capabilities of diverce bluetooth devices

The four association models are:
- *Just work*, no action required. No specific hardware capabilities are required, at least a button to initiate the procedure
- *numeric comparison*, user compares numbers displayed and confirm if both are same, require that both have a screen to show the number and a button to confirm
- *passkey entry*, at least one need a screen to show the number, and the other need a keypad or a screen with touchscreen keypad to enter the numbers
- *out of band*, typically using NFC


### Secure simple pairing
Describe the Bluetooth Secure Simple Pairing, showing the sequence of messages the two devices exchange to complete the pairing. (4 points).

Describe a possible Man In The Middle attack to such a scheme. (2 points) 

You can use a numbered list and state who sends what to who, or which computations a device does with some information:
1. A frame XXX to B 
2. B sends frame YYY to broadcast 
3. A extracts ZZZ from YYY and computes KKK, YYY, LLL 
4. ...


**solution**
secure simple pairing was introduced to improve secure, eliminates the fixed PIN code that was the weakness of older bluetooth versions and instead use public key cryptography

Here a basic scheme for authentication with public key cryptography

Alice has a PK and a SK
Alice tell Bob she wants to pair
Bob send back a challenge
Alice send the challenge encrypted with the SK
Bob ask for the PK
Alice send her PK
Bob decrypt the previous message, if the result is the challenge means 

In this scenario a MITM attack is possible
An attacker with his own PK SK can intercept the messages and act as Alice for Bob, so Bob will have attacker's PK. And act as Bob to alice, so alice will complete the procedure. If Bob send a message to Alice encypted with the PK (of attacker), the attacker can decrypt it, read it, encrypt it with the actual Alice PK and send it to alice. Alice and Bob will not notice anithyng

To overcome this problem SSP offers two user assisted numeric methods for authentication 
numerical comparision and paskey rentry