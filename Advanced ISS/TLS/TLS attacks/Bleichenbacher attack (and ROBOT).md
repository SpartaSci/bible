(1998) Daniel Bleichenbacher’s “million-message attack”

a [[cybersec/_problem/vulnerability|vulnerability]] in the way RSA encryption was done;

remember that, if the server has an RSA public key which can be used for encryption, the client encrypts the pre-master secret with such key before sending it to the server;

attacker can perform an RSA private key operation with a server’s private key by sending a million or so well-crafted messages and looking for differences in the [[cybersec/integrity/Error Correction Code|error codes]] returned (the error codes are leaking information regarding the bits of the server’s private key);

attack refined over the years and in some cases only requires thousands of messages (feasible from a laptop!);

(2017) ROBOT = variant of Bleichenbacher’s attack

affected major websites (including facebook.com);