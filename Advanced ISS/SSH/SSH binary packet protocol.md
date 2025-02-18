- packet length (4 bytes):
	- not including the MAC and the packet length field itself;
- payload (note - may be compressed):
	- size = packet length - padding length - 1;
	- max (uncompressed) size is 32768 byte;
- random padding:
	- 4 - 255 bytes;
	- total packet length (MAC excluded) must be multiple of max(8, cipher block size) . . . even if a stream cipher is used (!);
- MAC (as part of the authenticate-and-encrypt schema)
	- computed over the cleartext packet and an implicit sequence number;
		- since we’re over TCP we have protection against both replay and filtering attacks;
	- requires decryption before checking integrity (possible DoS!);



![[Advanced ISS/_images/SSH_binary.png]]
