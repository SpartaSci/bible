# Circuit-Level Gateway

> it is a **transparent** proxy firewall (transparent because is the socket to be controlled by the gateway) that works at TCP/UDP level and blocks the direct TCP/UDP connection to the server in order to protect to TCP handshake attack and to protect to IP fragmentation. An example of circuit-level gateway is SOCKS.

###### Socks
SOCKS (short for SOCKetS) is a network protocol for implementing circuit gateways.  The first version of SOCKS was implemented by Dave Koblas and Michelle Koblas in the early 1990s. SOCKS consists of three components: the SOCKS server, the SOCKS client, and the SOCKS client library.

The SOCKS server runs on a packet filtering firewall through port 1080. The SOCKS client library runs on an internal host, and the SOCKS client runs on an external client host. The SOCKS client executes the modified versions of FTP and other standard TCP based client application programs, which are modified for SOCKS.

When an external client wants to obtain service from an internal server under the protection of SOCKS, the client must first establish a TCP connection with the SOCKS server.

It then negotiates with the SOCKS server to select an authentication algorithm, provides information for authentication, and submits a relay request.

The SOCKS server verifies the information submitted for authentication and determines whether to establish a relay connection with the internal server as requested.
