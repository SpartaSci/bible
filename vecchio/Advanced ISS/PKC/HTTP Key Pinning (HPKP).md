### HTTP Key Pinning (HPKP)

The owner of a website that wants to protect against the above problems can try HTTP Key Pinning. Since it is not possible to avoid some CAs being subverted or some fraud taking place, it is possible to specify, when a client connects with the server, the digest of the public key of the server. Even if the certificate is sent, since there could be many fake certificates, the server will inform the client that this is the correct one through the digest of the public key. 

The user agent (UA), or browser, will cache the key and refuse to connect to a site with a different key. This method is a TOFU technique (Trust on First Use), so it works only if the first server to which the user connects is the real one; otherwise, clients will accept only the fraudulent one. It is important to manage key updates properly, usually including a backup key. URIs are sent to the owner when clients connect with fake ones. 

Given all the problems with this solution, HPKP is not widely used today, and the Certificate Transparency approach is preferred.
