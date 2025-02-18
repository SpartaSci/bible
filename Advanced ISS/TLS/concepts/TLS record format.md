![](https://peelingrage.netlify.app/static/5a454f9e9fedcd24dec5272c261c8f52/b9e4f/tls_record_general.png)



it’s a 5-byte header;


uint8 type = change_cipher_spec (20), alert (21), handshake (22), application_data (23);

uint16 version = major (uint8) + minor (uint8);

uint16 length:
- ≤ 214 (record not compressed) for compatibility with SSL-2;
- ≤ 214 + 1024 (compressed records);


• plus a payload (max 16 kB);



