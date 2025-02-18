### Time-stamping

Time-stamping is crucial in workflows related to signing documents because it helps **establish that a document existed before a certain point in time**. However, it is important to note that timestamping does **not** provide the date when the document was created, but rather it proves that the data existed before a certain time. In other words, it shows that the data was present at a specific moment, but the exact creation time remains unknown—only that it was created before the timestamp.

Time-stamping is usually handled by a **Time-Stamping Authority (TSA)**, which follows a specific protocol and data format. **RFC-3161** defines the **Time-Stamp Protocol (TSP)** for requests and the **Time-Stamp Token (TST)** format for the proof.

#### How Time-stamping Works:
- A user has some data created at some point in time (this data could be anything—encrypted data, plain text, a signed document, etc.).
- The user wants to prove that the data existed at a specific time. To do this, the user computes a **hash** of the data (instead of sending the actual data for privacy reasons) and sends it to the TSA.
- The TSA receives the hash, consults a very precise clock, and creates the **TST**. This token contains:
  - The hash (digest) of the data
  - The current date and time
  - The TSA’s **digital signature** of this information

The TSA signature (`dsig(TSA)`) is applied to the **digest** and **date**, not to the actual document. This binds the hash and timestamp together. The entire token (TST) is returned to the user, who can then attach it to their data. If the data is modified after the TST is received, the change will be detected because the hash will no longer match. 

This process is particularly useful in cases where deadlines need to be met, as it allows the user to prove that their data existed before a certain deadline.

#### Time-stamping and Signatures:
Timestamping does not indicate when a document was signed but only that the document existed before the timestamp. However, if you want to prove when a signature was created, you can use **two timestamps**.

Looking at the process:
1. The document's hash is sent to the TSA, and the **TST1** token is issued.
2. The document and **TST1** are combined, and a signature is created over this combination.
3. The hash of the signed document plus **TST1** is sent to the TSA, which creates a **TST2**.

This approach demonstrates that:
- The document existed before the time in **TST1** (e.g., the document existed before 15:00).
- The signature was created between the timestamps in **TST1** and **TST2** (e.g., the signature was created between 15:00 and 15:03).

However, even with this method, it is still not possible to determine the exact time the document was originally created.

In Italy, time-stamping is referred to as **"marca temporale"**.
