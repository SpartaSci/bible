Given an encrypted packet the attacker can recover the original content by altering **one byte at a time**. 

It is always possible to create a corrupted packet based on a captured packet, which will be accepted by the AP

The chop chop attack works by chopping off the last byte of the sniffed packet.  This packet will not be accepted by the AP (the ICV checksum is not correct)

After chopping it off, modify one byte of this packet until it becomes corrected again. We test this by injecting our new packet into the network and seeing if it was accepted or rejected be the AP.

If it is accepted, the AP will send it back out into the wireless network and we will have the validation that our guessed byte was correct.

Repeat it for all bytes and it can be used to build more complex attacks.
