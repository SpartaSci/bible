# SSH remote port forwarding
forwards traffic from a remote port at the SSH server to a local port of the SSH client;
(example) you want to let an external user connect to your local HTTP server (which is behind a NAT). With the command

ssh -R 8000:127.0.0.1:80 user@ssh server

the traffic to port 8000 of ssh server will be remotely (-R) forwarded to port 80 of the SSH client (the HTTP server) using a tunnel. The SSH server offers a generic listening service on port 8000 (this can be whatever port is available for listening and not necessarily port 8000);


![[Advanced ISS/_images/SSH_remote_port_forwarding.png]]

