HMAC-based extract-and-expand Key Derivation Function

HKDF(salt,IKM,info,length) = HKDF-Expand(HKDF-Extract(salt,IKM),info,length);


1. the first stage takes the **input keying material (IKM)** and “extracts” from it a fixed-length **pseudorandom key (PRK)**

2. then the second stage “expands” this key into several additional pseudorandom keys (the output of the KDF);
	- multiple outputs can be generated from a single IKM value by using different values “info” field (which is just a string);
	- repeatedly call HMAC using the PRK as the key and the “info” as the message; the HMAC inputs are chained by prepending the previous hash block to the “info” field and appending an incrementing 8-bit counter;


# HKDF usage in TLS 1.3

```
HKDF-Expand-Label(Secret,Label,Context,Length)=HKDF-Expand(Secret,HkdfLabel,length);

```
where HkdfLabel is:
```
struct {
	uint16 length = Length;
	opaque label<7..255> = "tls13" + Label;
	opaque context<0..255> = Context;
} HkdfLabel;
```

```
Derive-Secret(Secret, Label, Messages) = HKDF-Expand-Label(Secret, Label, Transcript-Hash(Messages), Hash.length)

```

finished_key = HKDF-Expand-Label(BaseKey, “finished”, “”, Hash.length);
- “finished” message key;

ticket_PSK = HKDF-Expand-Label(resumption_master_secret, “resumption”, ticket_nonce, Hash.length);
- session ticket pre-shared key;




[[Advanced ISS/TLS/TLS-1.3/TLS 1.3 key schedule|TLS 1.3 key schedule]]
