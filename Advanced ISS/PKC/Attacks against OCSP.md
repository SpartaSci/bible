### Some attacks against OCSP are:

- **Replay attack**: it is possible to copy the whole response saying that the certificate is valid and replay it after the certificate is revoked.  
  If the question is, “Is certificate number 23 valid?” and it has been answered in the past, it is possible to take an old answer for that certificate and replay it. But if there is also the date and time in the question, the attacker cannot reply with an old answer.  
  To defend against this attack, something is needed that strictly relates the answer with the question, which is typically a nonce.

- **DoS attack**: by relying on the OCSP, it is possible to try to flood the server with many requests, because each request requires a signature in real-time, which is a heavy process.  
  The defense is to pre-compute responses and include three timestamps:
  - **thisUpdate** – the response is based on revocation information available now.
  - **nextUpdate** – is again a promise.
  - **producedAt** – this answer was created at this moment.

These answers are created even if no question is made. Since we are creating the answer without waiting for the request, there is no nonce.  
In order to protect from DoS attacks, this approach creates a problem regarding replay attacks. Some companies use pre-computed responses and try to make them fast enough (e.g., the response is valid only for 30 minutes). Again, there is the need to look at the policy.
