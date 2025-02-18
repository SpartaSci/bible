

Key generation requires complex algorithms and often RNG (Random Number Generation). After generation, the private key needs to be protected:

- **When it is stored**: if someone copies our private key, they will be able to identify us.
- **When it is used**: when we use the private key to perform operations like digital signatures or decryption, we need to provide the private key to some computational engine (such as the CPU). If the CPU is infected with malware, the private key will be compromised.

The generation and use of a key pair can be performed by a **software** application. For example, all browsers have the capability to generate a key-pair. However, computers may be infected with malware, and there may be weak keys (if the algorithm for generation is not properly implemented). For this reason, we don’t rely directly on the browser but use **dedicated hardware** (e.g., RSA smart card). However, in this case, there are problems with updating algorithms and mechanisms, and it is difficult or impossible to release a vulnerability patch since hardware updates are generally difficult.

A third solution for key-pair generation is to generate the keys using well-implemented software and then **inject the private key inside a hardware secure device**. This is often the case when giving keys to employees. If the private key is under the control of the employees, there is a problem: if an employee uses the key to encrypt important data and later leaves the company, you may not be able to access the data. In these cases, the company will give the keys, but a copy of those keys will be stored within the company (e.g., in case the employee loses the key). 

This third solution is acceptable if the key is restricted to perform encryption only and not digital signatures, as there is a problem with non-repudiation since both the company and the employee know the private key. The most common solution is to have two key pairs: 

1. **One for digital signatures**, which is associated with non-repudiation (the private key is yours and only yours).
2. **One for encryption**, which may be subject to key recovery to help recover the data if you lose control of the private key.
