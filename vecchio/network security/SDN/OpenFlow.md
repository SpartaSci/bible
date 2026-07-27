> OpenFlow is a protocol and it is the first implementation of [[network security/SDN/_SDN - Software Defined Networking|SDN]]. 

Allows to:
- send forwarding rules to the switches
- receive from the switch the packets that may not match any rules in the switches
- inject packets in the switches
- ask for switch statistics and get data back to analyze them further




SDN switches *can be configured*, in OpenFlow, in two modes:
- **Reactive configuration**: some packets are sent to the controller and cause the insertion of new flow entries; this cause a small additional delay due to the flow setup time. Moreover, this type of configuration allows an efficient use of the flow table because only needed forwarding rules are configured. If control connection lost, switch can forward only packets for which rules are configured before connection lost (potential disrupt traffic).
- **Proactive configuration**: the controller pre-populates flow tables in the switches; so, zero additional flow setup time is needed. If control connection lost, there is no traffic disruption because flow tables are pre-configured.

Moreover, the *routing* can be made, in OpenFlow, in two modes:
- **Fine-grained routing**: matching is done at a very fine granular level and the flow tables contain one entry per flow. This type of routing is good for fine grain control (e.g. for campus networks or datacenters).
- **Aggregated routing**: one forwarding rule (flow entry) covers a large group of flows. For the purpose, wildcard flow entries (or also called wildcard rules) are used. This type of routing is good for large number of flows (e.g. for backbone).



>A **flow rule** is a traffic flow abstraction that can connect two arbitrary OpenFlow (OF) switch ports and may cross multiple OF switches. Each flow rule is isolated from the other flow rules.

>A **flowmod** is an OF message used to instantiate, modify or delete a flow rule on a single switch.

A single **flow rule** is composed by:

- **Match**: list of fields used to match against packets. These fields are ingress and egress port, IPv4 or IPv6 or ETH source and destination addresses, TCP or UDP source and destination ports. Numbers of supported fields changes across different OpenFlow versions.
- **Priority**: matching precedence of the flow entry; the matching process starts with the flow rules at higher priority. If no matches are found, rules at the highest minus 1 priority are analyzed and so on, until a match is found. The priority value uses 6 bit to be expressed.
- **Actions**: list of actions that are applied to the packet in case of matching. There are the forward, the drop, the overwrite header field (acting as a [[network/NAT - Network address translation|NAT]] for example), the push/pop field (e.g. add or remove a VLAN tag, MPLS labels or [[network security/VPN/L3 - IPsec/GRE - Generic Routing Encapsulation|GRE]] keys) or the forward at a specific bit-rate actions (this action avoids to overload the network, maybe using a lower bit rate). Multiple actions can be supported in the same match.
- **Counters**: statistics related to the specific flow which are updated in case of match.
- **Timeouts**: maximum amount of time or idle time before flow is removed by the switch.
- **Cookies**: value chosen by the controller to filter flow entries affected by flow statistics, flow modification and flow deletion requests. This field is not used when packets are processed.
- **Flags**: they alter the way in which flow entries are managed.