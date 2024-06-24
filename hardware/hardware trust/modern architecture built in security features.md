

**Integrity and Safety** 
- *CRC*: used to verify data transmission or storage integrity
- *Power Supply Integrity Monitoring*: Ultra-safe supply monitoring. Several flag statuses to determine what causes a reset
- *Read While Write*: Efficient tamper detection logging
- *Clock Security System (CSS)*: Independent clock sources and recovery systems. Internal clock for secure program execution
- *Error Correction Code ([[cybersec/integrity/Error Correction Code|ECC]])*: Robust memory integrity. Hardened protection against [[hardware/attack taxonomy/fault attacks/_fault attacks|fault injection attacks]]
- *Parity Check*: Memory content integrity check
- *Temperature Sensor*: Check if the device operates in the expected temperature range. Protection against temperature or laser attacks
- *Watchdogs*: Independent watchdog and window watchdog for software timing control

**Crypto**
- *Random Number Generator*: On-chip entropy generation. Ensure strong keys and protect against replay attacks.
- *Hashing Functions & HMAC*: The Hash algorithm provides a way to guarantee the integrity of information, verify digital signatures and message authentication codes
- *Symmetric Cryptography*: various cryptography algorithms implemented in both hardware and software
- *Asymmetric Cryptography*: RSA signature function. ECC (Elliptic Curve Cryptography)

**Debug Access Protection**
- *JTAG or SWD*: Prevent unauthorized access to the device through debug interfaces.


**Tamper Protection**
- *Anti-Tamper*: Protect against a wide range of physical attacks on HW system outside the MCU
- *Backup Domain*: Maintains active tamper protection even in low power modes.
- *RTC (Alarm Timestamp)*: Timestamp on tamper event
- *Backup Register*: For Confidential data storage. Tamper automatically deletes registered content
- *GPIO Configuration Locking*: Lock the selected GPIO. It is impossible to unlock until the next reset. It is possible to lock communication channels after tamper detection.


**Privileges Permission Management**:
- *Memory Protection Unit (MPU)*: Divides the memory map into several regions with privilege permissions and access rules.
- *Firewall*: Even more restrictive than MPU. Made to protect a specific part of code or data from the rest of the code executed outside the protected area.

**Memory Protection**
- *Read Protection (RDP)*: Global memory access control management. It prevents memory dumps and safeguards users' IPs.
- *Write Protection (WRP)*: Each sector can be protected against unwanted write operations.
- *Proprietary Code Protection (PCROP)*: Each Sector can be configured in “execute only”.
- *Mass Erase*: Safely remove IPs and confidential data. Force factory reset.

**Traceability**
- *Device electronic 96-bit Unique ID*: Enables product traceability. Can be used for security key diversification.

**Secure Firmware Update**
- *Software SFU*: Secure firmware upgrade capability. Allows for different types of software updates with integrity check capabilities.