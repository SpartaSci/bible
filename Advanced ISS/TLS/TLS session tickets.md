---
tags:
  - extension
---
Since session resumption requires a **session-id cache** on server side which may become very large for high traffic servers, this extension was introduced to avoid using the session-id:

RFC-5077
**TLS session ticket** is an extension allowing the server to send the session data to the client:
- encrypted with a server secret key;
- returned by the client when resuming a session (so that the server can decrypt it and recover the negotiated algorithms and parameters);

in practice, it moves the session cache to the client so that the server only needs to store the secret key;


> [!attention] Issues
> - needs support at the browser (it’s an extension!)
> - in a load balancing environment, it requires key sharing among the various end-points (and periodic key update!);