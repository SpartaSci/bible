# Application-Level Gateway
An application-level gateway, also called an **application proxy**, acts as a relay of application-level traffic.

Source contacts the gateway using a TCP/IP application (e.g, HTTP, FTP, etc) and the gateway asks the user for the name of the remote host to be accessed.

When the source responds and provides a valid user ID and authentication information, the gateway contacts the application on the remote host and relays TCP segments containing the application data between the two endpoints.

If the gateway does not implement the proxy code for a specific application, the service is not supported and cannot be forwarded across the firewall.

Further, the gateway can be configured to support only specific features of an application that the network administrator considers acceptable while denying all other features.



> [!done] advantages
> 
Application-level gateways tend to be more secure than packet filters. 
Rather than trying to deal with the numerous possible combinations that are to be allowed and forbidden at the TCP and IP level, the application-level gateway need only scrutinize a few allowable applications. 
In addition, it is easy to log and audit all incoming traffic at the application level.
Summary:
-Can perform user-level authentication
-Can do intelligent (application specific) filtering
-Can be combined with caching
-Can do good logging

> [!danger] Disadvantage
A prime disadvantage of this type of gateway is the additional processing overhead on each connection.
There are two spliced connections between the end users, with the gateway at the splice point, and the gateway must examine and forward all traffic in both directions.
Require different servers for each service, Delay in supporting new application, Heavy on resources
Require modifications to clients
