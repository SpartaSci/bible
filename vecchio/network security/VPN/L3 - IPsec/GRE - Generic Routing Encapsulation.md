---
tags: 
aliases:
  - GRE
---


The Generic Routing Encapsulation (GRE) aims to encapsulate (tunneling) any protocol (including IP) into IP. There are two versions of GRE with their related headers. 
Both versions have some fields in the header:
- **C, R, K, S bits**: flags indicating the presence/absence of optional fields.
- **s bit**: strict source routing flag. If it is equal to 1, a field called Routing will contain the sequence of router IP addresses or ASs for source routing.
- **Recur**: maximum number of additional encapsulation permitted (must be 0).
- **Protocol Type**: ID of the payload protocol.

The new features introduced by the Enhanced GRE (version 1) are:
- **Payload length**: 16 bits that indicate the number of bytes excluding GRE header.
- **Call ID**: 16 bits that indicate the session ID for this packet.
- **Sequence number**: for ordered delivery, error detection and correction.
- **Acknowledge number**: a cumulative ACK that indicates the highest number of GRE packet received in sequence for this session.

Moreover, GRE allows to perform flow control (sliding window mechanism), to manage the out-of-order packets that are simply discarded, to recompute each time an ACK packet is received a new timeout value and to perform congestion control. By the way, GRE is a protocol at layer 3 and not at layer 4