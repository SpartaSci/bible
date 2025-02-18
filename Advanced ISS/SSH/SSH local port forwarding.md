# SSH local port forwarding
- forwards traffic from a local port to a remote port;
- example (picture below)
	- suppose to be behind a firewall that blocks access to an external mail server because only securetraffic is permitted;
	- by entering the command
		- ssh -L 1234:mail server:25 user@ssh server
		- the traffic to port 1234 on the (internal) client will be locally (-L) forwarded to port 25 on the mail server by using a tunnel to the (external) ssh server. user must be a valid user of ssh server;
	- now configure the Mail User Agent (MUA) to connect to localhost:1234 as outgoing mail server;
- having an SSH server on a different machine than the one which hosts the mail server doesn’t provide full protection to exchanged emails. This schema only bypasses the firewall but, between the SSH server and the mail server, the mail is not confidential anymore;

![[Advanced ISS/_images/ssh_local_port_forwarding.png]]



to avoid any insecure path, you should have the SSH server hosted on the same node as the application server (or have both hosted inside the same trusted subnet)
this is the best solution but it requires cooperation from the application server manager (in order to put both the SSH server and the mail server on the same machine);

![[Advanced ISS/_images/ssh_local_port_forwarding2.png]]
