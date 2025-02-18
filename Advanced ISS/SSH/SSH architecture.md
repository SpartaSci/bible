
Three-layer architecture:
- Transport Layer Protocol provides 
	- initial connection
	- server authentication
	- confidentiality and integrity with [[Advanced ISS/TLS/concepts/perfect forward secrecy|perfect forward secrecy]]
	- key re-exchange (RFC-4253 recommends after 1GB of data transmitted or after 1 hour of transmission)
		- TLS does not support re-keying (you must open a new connection in the same session or, even better, start a new session). In order to exchange keys again, TLS must break the channel (SSH doesn’t break the channel);
- User Authentication Protocol 
	- authenticates the client to the server
- Connection protocol
	- supports multiple connections (channels) over a single secure channel (implemented with the Transport Layer Protocol)
	- TLP is like a super channel which can be split into many sub channels. In TLS you can only have 1 active connection at a time inside the same session. Here, you can have simultaneously as many connections as possible within the same session;



> [!NOTE] TLP
> TLP is not TCP, nor UDP but it actually works on top of TCP, which is a reliable transport layer protocol. So, the name “Transport Layer Protocol (TLP)” may create a bit of confusion but it was called like this because its purpose is transporting information for user authentication and connection;
