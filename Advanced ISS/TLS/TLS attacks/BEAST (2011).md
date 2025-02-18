SSL channel using CBC with IV concatenation;

instead of generating a new IV every time, it uses the last block of the previous encryption as IV (so there is a concatenation);


this problem was fixed with TLS-1.1;
- a MITM may decrypt HTTP headers with a blockwise-adaptive chosen-plaintext attack;
- the attacker may decrypt HTTPS requests and steal information such as session cookies;