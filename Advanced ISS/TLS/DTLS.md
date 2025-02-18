We’ve said TLS can only be used on top of a reliable transport protocol, but is it possible to use it on top
of protocols such as UDP anyway? For that purpose, DTLS is used:
• Datagram Transport Layer Security (RFC-4347);
• applies the TLS concepts to datagram security (e.g. UDP);
• doesn’t offer the same properties as TLS:
– e.g., there’s no implicit sequence number (since datagrams can be lost);
• competition with IPsec and application security;
• example - SIP (Session Initiation Protocol, used to create a session for VoIP) security:
– with IPsec;
– with TLS (only for SIP_over_TCP);
– with DTLS (only for SIP_over_UDP);
– with secure SIP;

