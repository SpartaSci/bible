RFC-4346 (April 2006);

to protect against CBC attacks:
- the implicit IV is replaced with an explicit IV;
- padding errors now use the bad_record_mac alert message (rather than the decryption_failed one, used to distinguish between padding and non-padding errors) in order to not leak the specific reason why an error has occurred. This avoids the case where an attacker sends forged messages with different padding in order to understand how the server responds;


IANA registries defined for protocol parameters;

premature closes no longer cause a session to be non-resumable (it would be stupid to not be able to resume a session in case of network errors);

additional notes added for various new attacks;