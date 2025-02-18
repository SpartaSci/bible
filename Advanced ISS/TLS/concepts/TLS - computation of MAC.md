[[Advanced ISS/TLS/concepts/TLS record format|TLS record format]]

MAC = message_digest (key, seq_number || type || version || length || fragment)


**message_digest**: depends on the algorithm which was agreed during the [[Advanced ISS/TLS/concepts/TLS handshake protocol|TLS handshake protocol]]


**key**: sender-write-key or receiver-read-key 

> [!attention] the key is different for each direction
if the key is the same for both directions an attacker could make a copy of a record with a certain sequence number and inject it in the opposite direction, assuming that the recipient hasn’t received a record with that sequence number yet;

**seq_number**: 64-bit integer (never transmitted but computed implicitly):

$2^{64}$ records can be exchanged before an overflow occurs and the channel has to be closed and re-opened;

cancellation is detected because of the computation of the MAC with the implicitly computed sequence number (e.g., if the currently computed and expected sequence number is equal to 2, the MAC will be computed with that sequence number...and if an attacker has cancelled record number 2 the receiver will receive record number 3 which obviously has a different MAC);