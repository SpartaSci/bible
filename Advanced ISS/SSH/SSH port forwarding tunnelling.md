
- a way to forward TCP traffic through SSH
	- e.g. securing POP3, SMTP and HTTP connections
		- the connection protocol is already protected because it’s inside TLP;
		- insecure connections;
	- the client-server applications will run their normal authentication over the encrypted tunnel;
- there are two types of port forwarding:
	- local forwarding (outgoing tunnel);
	- remote forwarding (incoming tunnel);
	- both use the Connection Protocol to encapsulate a (or more) TCP channel inside a SSH one;
- TLS vs. SSH (IMPORTANT):
	- in TLS, session is only conceptual and the real traffic is inside the connection;
	- in SSH, TLP is already an exchange of data (and you normally use TLP if you have a direct connection from client to server) but, if that channel is actually a tunnel, we have TLP with the Connection Protocol inside it.


So, the Connection Protocol is not autonomously protected but it’s protected only because it’s inside TLP! So, this is not a channel with encryption, authentication, etc... but it’s simply a TCP channel inside TLP. That’s why we can have many active sub-channels inside TLP simultaneously (because they’re all TCP channels);


