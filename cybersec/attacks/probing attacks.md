

probing = sondare

Probing attacks are an invasive method for bypassing security measures by observing the physical silicon implementation of a chip. As an invasive attack, one directly accesses the internal wires and connections of a targeted device and extracts sensitive information. In combination with reverse engineering, this poses a serious threat. A typical probing attack will begin with decapsulation to expose the silicon die. Once done, an attacker can begin reverse engineering the device. By extracting the netlist, one can begin to understand the functionality and identify signals to target. Once the attacker finds a targeted signal and can map them to coordinates on a device, they can begin milling. By milling they expose the internal wires of the device. They can then form an electrical connection and begin extracting information. In order to protect against such attacks, it is important for a designer to identify possible targets and take appropriate measures. Examples of such targets can include the following:

- Encryption keys
- Firmware and configuration bitstreams
- On-device protected data
- Cryptographic random numbers

Some common countermeasures include shields and t-private circuits. Shields contain a layer of wires whose signals are monitored for disturbances caused by milling. T-private circuits aim to split signals up in order or exhaust an attacker’s resources by requiring them to use t + 1 number of probes to extract 1 bit of information. Other methods include light sensors to detect decapsulation and scrambling wire signals to prevent repetitive patterns.