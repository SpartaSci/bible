### What to Do with PKC Mistakenly Issued or Issued by Compromised CA

It is difficult for domain owners to detect certificates fraudulently issued for their domain (servers). For example, imagine that we are the manager of servers of Politecnico di Torino. If a certificate is received, everything is good and goes well. If an attacker goes to another CA and can create a certificate for Politecnico di Torino, is it possible to be informed of that? No, it is not possible. That was an error; the person was not authorized by Politecnico, yet the attacker has a valid certificate. If a client connects to the wrong server which contains a valid certificate, the browser is not able to detect that. Browsers aren’t good at detecting rapidly malicious websites if they receive (e.g., in a TLS connection):

- Mistakenly issued certificates
- Certificates issued by a compromised CA

If there is a certificate issued by mistake, it takes time to detect the problem, and it is needed to revoke all the certificates and make the browser aware of this problem. Until then, the browser thinks it is connected to the real server, so some attacks arise:

a. Fake server  
b. MITM attacks


### Mistakenly Issued Certificates: Some Examples

**2011:** An intruder managed to issue itself a valid certificate for the domain **google.com** and its subdomains from the prominent Dutch Certificate Authority DigiNotar. The certificate was issued in July 2011 but may have been used maliciously for weeks before detection on August 28, 2011, because it was used for large-scale MITM attacks on multiple users in Iran. Again, there is suspicion of a secret service operation, as spying on clients using Google services is not easy. However, if a fake website is created, it is possible to have, e.g., a fake Gmail and use it to spy on users by redirecting their traffic to the real Google server and acting as MITM.

**2011:** The Comodo Group suffered from an attack that resulted in the issuance of nine fraudulent certificates for various domains owned by Google, Yahoo!, Skype, and others.

**July 2014:** An unknown number of mis-issued certificates were issued by a sub-CA (one level down from the root CA) of India CCA, the Indian NIC (Network Information Center). Due to the scope of the incident, in which numerous certificates were created, the sub-CA was wholly revoked, and India CCA was constrained in the future to a subset of India’s top-level domains namespace. For example, they can no longer issue certificates for anything that ends with “.in,” but only for specific domains.
