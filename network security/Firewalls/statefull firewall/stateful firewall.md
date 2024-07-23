# Stateful firewalls
A traditional packet filter makes filtering decisions on an individual packet basis and does not take into consideration any higher-layer context.
To understand what is meant by context and why a traditional packet filter is limited with regard to context, a little background is needed.
Indeed, most standardized applications that run on top of TCP follow a client/server model.

**State keep track of the connection status**
- TCP is implemented with sequence numbers
- UDP is implemented just with the tuple <saddr,sport,daddr,dport>

**Able to filter on the connection state**
- Only the first packet of the connection
- All the other packets of the connection

**Examples of state-based forwarding decisions:**
- Is the packet a response to an earlier packet?
- Do the number of packets seen from some host exceed a threshold?
- Is the packet identical to a recently seen packet?
- Is the packet a fragment?


Stateful filtering, also referred to as connection-state filtering, keeps track of connections between an internal host and an external host.

A connection state (or state, for short) indicates whether it is a TCP connection or a UDP connection and whether the connection is established, and are stored in a state table.

When a packet arrives, whether it is an ingress packet or an egress packet, the stateful filtering firewall checks whether the packet belongs to an existing connection against its state table.
- If yes, the firewall allows the packet to pass through and saves the information (such as its TCP sequence number) for later use.
- If the packet is a SYN packet, the firewall creates a new entry in the state table.
- If the packet does not belong to an existing connection and it is not a SYN packet, the firewall will discard it.
- When a network connection ends, the connection state is removed from the state table.

#### iptables
iptables manages states with the following rules:

iptables -A INPUT -p tcp –dport 22 -m conntrack --ctstate NEW -j ACCEPT
- This rule means that iptables accepts TCP packets (dport = 22), and it saves a local state when a packet of this type is received.

iptables -A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
- This rule means that iptables accepts packets related to an established/related communication for which there is a state (e.g., all the packets related to the communication expressed in rule 1), or expressed in other rules of type -m conntrack --ctstate NEW)
#### ipfw
ipfw manages states with the following rules:

ipfw -q add allow tcp from any to any 80 out via tun0 setup keep-state
- This rule means that ipfw accepts TCP packets (dport = 80), and it saves a local state when a packet of this type is received.
ipfw -q add check-state
- This rule means that iptables accepts packets related to an established communication for which there is a state (e.g., all the packets related to the communication expressed in rule 1), or expressed in other rules of type keep-state)
