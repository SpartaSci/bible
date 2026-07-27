PKI Needed for Server and (Optionally) Client Authentication, Unless **PSK authentication** is adopted.

**When a Peer Sends Its Certificate**:
- The **whole chain** is needed except the root CA (beware!).
  - If a chain that includes a root CA is accepted (by poorly implemented peers), that root CA may be added to the list of trusted CAs, which would be a disaster.
    - Fake root CAs would be accepted and considered valid just because they’re self-signed.
- **Validate the whole chain** (not just the EE certificate), except the root CA (if present).
- **Revocation status** is needed at each step of the chain.

**To Check Revocation Status:**
- **Certificate Revocation List (CRL)** can be used, but has:
  - Large size and lengthy look-up times.
- **Online Certificate Status Protocol ([[Advanced ISS/TLS/TLS-1.3/OCSP stapling|OCSP]])** can be used, but:
  - **Generates privacy problems** (leaks client navigation history).
    - The protocol only indicates if the certificate is valid at that specific moment (when the request is sent to the OCSP server).
    - This is not an issue since in TLS we check certificate validity specifically when creating a connection.
  - **Privacy issue**: if the client uses OCSP to validate the server’s certificate, the OCSP server will know which website the client is visiting (the one hosted on the server S).
  
**Performance Considerations**
- Both methods require one additional network connection and **add delay** (e.g., for OCSP: +300ms median, +1s average), which is obviously a bottleneck in the setup of a TLS connection.

# TLS and certificate status


> [!question] what if the URL for CRL or OCSP is unreachable?
> we experience a huge delay, equal to two times the maximum RTT, because when we try to open a TCP channel and we don’t get any answer, since the request could’ve been lost in the network, we have to wait twice the maximum distance in the Internet. What happens when the timeout elapses? What should we do?


possible causes:
- server error;
- network error;
- access blocked by firewall (e.g. due to security policy or insecure channel - typical for OCSP);

possible approaches:
- hard fail: page is not displayed + security warning;
- soft-fail: page is displayed (assuming certificate is good);
	- assuming the certificate to be good is obviously risky (e.g., shadow server blocking connection to OCSP server to not provide the client with any answer and let it accept the certificate);
- both hard and soft fail require additional load time (wait for the connection to time out);



## pushed CRL

- Revoked certificates are often the result of a compromised intermediate CA.
  - No need to populate the CRL with all certificates. By revoking the "father" certificate, all child certificates will be automatically revoked.

### Browser Vendor Approaches to Revoked Certificates

**Internet Explorer** (with browser update - not ideal, can be blocked):
- The CRL is updated only when there’s an Internet Explorer update.
- An attacker may block traffic to the Windows Update process, preventing the software from being updated.
- On the other hand, **Firefox** keeps trying to update.


**Firefox** - oneCRL (part of the blocklisting process):
  - Firefox maintains a connection to a Firefox server and regularly checks for CRL updates. Even if the connection is blocked, Firefox will continue trying periodically. If the update continues to fail, the user will receive a notification.
  - Firefox provides CRL information in JSON format:
    ```bash
    $ curl https://firefox.settings.services.mozilla.com/v1/buckets/security-state/collections/onecrl/records > crl.json
    ```
  - A JSON query program can be used to extract needed information from the file. Example Linux command:
    ```bash
    $ jq '[.data[] | {enabled,issuerName,serialNumber} | select(.enabled) | del(.enabled)]' crl.json > crl_short.json
    ```



**Chrome** (and **Edge**, **Opera** - as they share the Chromium kernel) - `CRLsets`:
  - CRLs from Chrome can only be processed by installing the appropriate tools:
    - [CRLset Tools on GitHub](https://github.com/agl/crlset-tools)
