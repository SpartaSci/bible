# SSH: causes of insecurity
• direct trust in public keys (X.509 certs not used, but some commercial versions do and openSSH has
SSH certificates);
• users ignore warnings and blindly accept new server public key...which leads to MITM attacks;
• weak server platform security
– worms, malicious code, rootkits, etc...
• weak client platform security
– malware, keylogger, etc...
• any connection to a local forwarded port will be tunnelled...even if coming from another node (!)
– to avoid this behaviour, specify also the local bind address, e.g.
ssh -L 127.0.0.1:1234:mail server:25 user@ssh server
so that only local processes can use the tunnel;