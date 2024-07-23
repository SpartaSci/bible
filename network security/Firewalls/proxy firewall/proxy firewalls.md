In computer networking, a proxy server is a server application that acts as an intermediary between a client requesting a resource and the server providing that resource

Instead of connecting directly to a server that can fulfill a request for a resource, such as a file or web page, the client directs the request to the proxy server, which evaluates the request and performs the required network transactions.

**Open proxy**: it is a proxy that exists on the internet and it is not in our network

**Reverse proxies**:it is a proxy that is present in our internal network 
- Encryption/SSL acceleration
- Load balancing:
- Caching
- **Security (isolation)**


#### Breaks the client - server model
- More protection for the server
- May authenticate the client
- Not transparent to the client

#### Type of Firewall

##### Application-Level Gateway
An application-level gateway, also called an **application proxy**, acts as a relay of application-level traffic.

Source contacts the gateway using a TCP/IP application (e.g, HTTP, FTP, etc) and the gateway asks the user for the name of the remote host to be accessed.

When the source responds and provides a valid user ID and authentication information, the gateway contacts the application on the remote host and relays TCP segments containing the application data between the two endpoints.

If the gateway does not implement the proxy code for a specific application, the service is not supported and cannot be forwarded across the firewall.

Further, the gateway can be configured to support only specific features of an application that the network administrator considers acceptable while denying all other features.

###### Advantage

Application-level gateways tend to be more secure than packet filters.

Rather than trying to deal with the numerous possible combinations that are to be
allowed and forbidden at the TCP and IP level, the application-level gateway need
only scrutinize a few allowable applications.

In addition, it is easy to log and audit all incoming traffic at the application level.

Summary:
- Can perform user-level authentication
- Can do intelligent (application specific) filtering
- Can be combined with caching
- Can do good logging

###### Disadvantage
A prime disadvantage of this type of gateway is the additional processing overhead on each connection.

There are two spliced connections between the end users, with the gateway at the splice point, and the gateway must examine and forward all traffic in both directions.

Require different servers for each service
- Delay in supporting new application
- Heavy on resources
Require modifications to clients

##### Circuit-Level Gateway
- Circuit gateway is also referred to as a transparent proxy firewall
- A generic proxy that breaks the TCP/UDP connection
- Block the direct TCP/UDP connection to the server
- Protect to TCP handshake attack
- Protect to IP fragmentation

###### Socks
SOCKS (short for SOCKetS) is a network protocol for implementing circuit gateways.  The first version of SOCKS was implemented by Dave Koblas and Michelle Koblas in the early 1990s. SOCKS consists of three components: the SOCKS server, the SOCKS client, and the SOCKS client library.

The SOCKS server runs on a packet filtering firewall through port 1080. The SOCKS client library runs on an internal host, and the SOCKS client runs on an external client host. The SOCKS client executes the modified versions of FTP and other standard TCP based client application programs, which are modified for SOCKS.

When an external client wants to obtain service from an internal server under the protection of SOCKS, the client must first establish a TCP connection with the SOCKS server.

It then negotiates with the SOCKS server to select an authentication algorithm, provides information for authentication, and submits a relay request.

The SOCKS server verifies the information submitted for authentication and determines whether to establish a relay connection with the internal server as requested.

![[Applicationlevel.png]]
