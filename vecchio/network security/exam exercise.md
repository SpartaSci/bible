
remember
transport mode: only IP payload is encrypted/authenticated, is used to protect communication between two host (no gateway are involved)

tunnel mode: entire IP packet is encrypted/authenticated, then encapsulated in a new IP header. Used to create VPN and connect subnets


# mock

```
Structure of Security Policy
SP_ID, IP_Src, IP_Dst, Protocol(AH/ESP), Mode(Tunnel/Transport), SA_ID

Structure of Security Association
SA_ID, IP_Src, IP_Dst, Protocol(AH/ESP), Algorithm
```

<-> this means that two SA and SP are needed (both directions) 

analysis of the Requirements
- 1) G1 <-> G3 confidentiality, ESP, tunnel
- 2,3) H2 <-> G2 + G2 <-> G3 confidentiality, esp, tunnel 
	- (yes, only 'protect' in R3 means only confidentiality but during exam ask clarification anyway) 
- 4) H1a <-> S1 integrity, ah, transport
- 5) H1a <-> G1 + H1b <-> G1 + H1b <-> H1a confidentiality, esp, tunnel



Security policies -> sp

Security associations -> sa

## sol
**G1**

| SP_ID | IP_Src  | IP_Dst  | Protocol | Mode   | SA_ID |
| ----- | ------- | ------- | -------- | ------ | ----- |
| 1     | IP_Sub1 | IP_Sub2 | ESP      | Tunnel | 1     |
| 9     | IP_Sub1 | IP_h1a  | ESP      | tunnel | 9     |
| 10    | IP_sub1 | IP_h1b  | ESP      |        |       |

|SA_ID|IP_Src|IP_Dst|Protocol|Algorithm|
|---|---|---|---|---|
|1|IP_Sub1|IP_Sub2|ESP|AES-256|

---


**G2**

| SP_ID | IP_Src  | IP_Dst  | Protocol | Mode   | SA_ID |
| ----- | ------- | ------- | -------- | ------ | ----- |
| 2     | IP_Sub2 | IP_Sub1 | ESP      | Tunnel | 2     |
| 4     | IP_H2   | IP_Sub2 | ESP      | Tunnel | 4     |
| 5     | IP_Sub2 | IP_H2   | ESP      | Tunnel | 5     |



|SA_ID|IP_Src|IP_Dst|Protocol|Algorithm|
|---|---|---|---|---|
|2|IP_Sub2|IP_Sub1|ESP|AES-256|
|4|IP_H2|IP_Sub2|ESP|AES-256|
|5|IP_Sub2|IP_H2|ESP|AES-256|

---

**G3**

| SP_ID | IP_Src  | IP_Dst  | Protocol | Mode   | SA_ID |
| ----- | ------- | ------- | -------- | ------ | ----- |
| 8     | IP_Sub2 | IP_Sub1 | ESP      | Tunnel | 8     |

| SA_ID | IP_Src  | IP_Dst  | Protocol | Algorithm |
| ----- | ------- | ------- | -------- | --------- |
| 8     | IP_Sub2 | IP_Sub1 | ESP      | AES-256   |

---

**H2**

| SP_ID | IP_Src | IP_Dst  | Protocol | Mode   | SA_ID |
| ----- | ------ | ------- | -------- | ------ | ----- |
| 3     | IP_H2  | IP_Sub2 | ESP      | Tunnel | 3     |



| SA_ID | IP_Src | IP_Dst  | Protocol | Algorithm |
| ----- | ------ | ------- | -------- | --------- |
| 3     | IP_H2  | IP_Sub2 | ESP      | AES-256   |

---

**H1a**

| SP_ID | IP_Src | IP_Dst | Protocol | Mode      | SA_ID |
| ----- | ------ | ------ | -------- | --------- | ----- |
| 6     | IP_H1a | IP_S1  | AH       | Transport | 6     |


| SA_ID | IP_Src | IP_Dst | Protocol | Algorithm |
| ----- | ------ | ------ | -------- | --------- |
| 6     | IP_H1a | IP_S1  | AH       | SHA-256   |

---

**S1**

| SP_ID | IP_Src | IP_Dst | Protocol | Mode      | SA_ID |
| ----- | ------ | ------ | -------- | --------- | ----- |
| 7     | IP_S1  | IP_H1a | AH       | Transport | 7     |


|SA_ID|IP_Src|IP_Dst|Protocol|Algorithm|
|---|---|---|---|---|
|7|IP_S1|IP_H1a|AH|SHA-256|

---



# 2024-07-09
some info are missing on the Network diagram so i'm trusting RR solution

10.0.0.1 sends a ping to 10.0.0.4
in R1 
|IP_h1 | AH | IP_h2 | IP payload |
IP_h1 header (192.130.1.1 -> 192.130.2.4)
IP_h2 header  (10.0.0.1->10.0.0.4)

in R2 is the same since is in tunnel mode 


10.0.0.2 sends a ping to 10.0.0.3
in R1
| IP_h1 | IP payload |
IP_h1 header (10.0.0.2 -> 10.0.0.3)

in R2
| IP_h2 | ESP header | IP_h1 |IP payload| ESP trailer|
IP_h1 header (10.0.0.2 -> 10.0.0.3)
IP_h2 header (130.192.4.1 -> 130.192.4.2) (ip of the two gateway i suppose)


# 2024-07-23

| PF           |            |            |              |              |           |            |
| ------------ | ---------- | ---------- | ------------ | ------------ | --------- | ---------- |
| **Priority** | **IP_Src** | **IP_Dst** | **Port_Src** | **Port_Dst** | **Proto** | **Action** |
| 1            | A          | S2         | *            | 80           | *         | Allow      |
| 2            | S2         | A          | 80           | *            | *         | Allow      |
| default      |            |            |              |              |           | Deny       |

| FW1          |             |             |              |              |           |            |
| ------------ | ----------- | ----------- | ------------ | ------------ | --------- | ---------- |
| **Priority** | **IP_Src**  | **IP_Dst**  | **Port_Src** | **Port_Dst** | **Proto** | **Action** |
| 1            | 192.130.1.* | S2          | *            | 80           | *         | Allow      |
| 2            | S2          | 192.130.1.* | 80           | *            | *         | Allow      |
| default      |             |             |              |              |           | Block      |


| FW2          |            |            |              |              |           |            |
| ------------ | ---------- | ---------- | ------------ | ------------ | --------- | ---------- |
| **Priority** | **IP_Src** | **IP_Dst** | **Port_Src** | **Port_Dst** | **Proto** | **Action** |
| default      |            |            |              |              |           | allow      |

| FW3          |            |            |              |              |           |            |
| ------------ | ---------- | ---------- | ------------ | ------------ | --------- | ---------- |
| **Priority** | **IP_Src** | **IP_Dst** | **Port_Src** | **Port_Dst** | **Proto** | **Action** |
| default      |            |            |              |              |           | allow      |

| FW4          |            |            |              |              |           |            |
| ------------ | ---------- | ---------- | ------------ | ------------ | --------- | ---------- |
| **Priority** | **IP_Src** | **IP_Dst** | **Port_Src** | **Port_Dst** | **Proto** | **Action** |
| 1            | S2         | A          | 80           | *            | *         | Allow      |
| 2            | A          | S2         | *            | 80           | *         | Allow      |
| 3            | S2         | B          | 80           | *            | *         | Allow      |
| 4            | B          | S2         | *            | 80           | *         | Allow      |
| 5            | S1         | S2         | *            | 80           | *         | Block      |
| 6            | S2         | S1         | 80           | *            | *         | Block      |
| 7            | S1         | S2         | *            | *            | *         | Allow      |
| 8            | S2         | S1         | *            | *            | *         | Allow      |
| default      |            |            |              |              |           | block      |





# 2025-01-15

- 1) g1 <-> g3 integrity, AH, Tunnel
- 2) g1 <-> h1 conf, esp, tunnel
- 3) g3 <-> h2 conf, esp, tunnel
- 4) h2 <-> s2 integrity, ah tunnel (i think, since it says until G3)

- G1
	- SPs
		- 1, IP_subnet1, IP_subnet2, AH, tunnel, 1
		- 2, IP_subnet2, IP_subnet1, AH, tunnel, 2
		- 3, IP_H1, IP_subnet1, ESP, tunnel, 3
		- 4, IP_subnet1, IP_H1, ESP, tunnel, 4
	- SAs
		- 1, IP_subnet1, IP_subnet2, AH, SHA-256
		- 2, IP_subnet2, IP_subnet1, AH, SHA-256
		- 3, IP_H1, IP_subnet1, ESP, AES-256
		- 4, IP_subnet1, IP_H1, ESP, AES-256

- G3
	- SPs
		- 1, IP_subnet1, IP_subnet2, AH, tunnel, 1
		- 2, IP_subnet2, IP_subnet1, AH, tunnel, 2
		- 5, IP_H2, IP_subnet2, ESP, tunnel, 5
		- 6, IP_subnet2, IP_H2, ESP, tunnel, 6
		- 7, IP_H2, IP_S2, AH, tunnel, 7
		- 8, IP_S2, IP_H2, AH, tunnel, 8
	- SAs
		- 1, IP_subnet1, IP_subnet2, AH, SHA-256
		- 2, IP_subnet2, IP_subnet1, AH, SHA-256
		- 5, IP_H2, IP_subnet2, ESP, AES-256
		- 6, IP_subnet2, IP_H2, ESP, AES-256
		- 7, IP_H2, IP_S2, AH, SHA-256
		- 8, IP_S2, IP_H2, AH, SH-256
- H1
	- SPs
		- 3, IP_H1, IP_subnet1, ESP, tunnel, 3
		- 4, IP_subnet1, IP_H1, ESP, tunnel, 4
	- SAs
		- 3, IP_H1, IP_subnet1, ESP, AES-256
		- 4, IP_subnet1, IP_H1, ESP, AES-256
- H2
	- SPs
		- 5, IP_H2, IP_subnet2, ESP, tunnel, 5
		- 6, IP_subnet2, IP_H2, ESP, tunnel, 6
		- 7, IP_H2, IP_S2, AH, tunnel, 7
		- 8, IP_S2, IP_H2, AH, tunnel, 8
	- SAs
		- 5, IP_H2, IP_subnet2, ESP, AES-256
		- 6, IP_subnet2, IP_H2, ESP, AES-256
		- 7, IP_H2, IP_S2, AH, SHA-256
		- 8, IP_S2, IP_H2, AH, SH-256
 






