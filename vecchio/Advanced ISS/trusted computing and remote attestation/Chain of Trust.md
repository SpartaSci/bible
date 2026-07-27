

In a **chain of trust**, each component in a system measures the next component in sequence, validating its integrity before storing the result securely. Here’s how it typically works:

1. **Component A measures Component B**: Component A takes an integrity measurement of Component B, then stores the resulting hash in the Root of Trust for Storage (RTS).
   
2. **Component B measures Component C**: Following a similar process, Component B performs integrity checks on Component C, storing these results in the RTS.

3. **Verification Process**: A trusted component, known as the Root of Trust for Reporting (RTR), retrieves the measurements stored in the RTS. When the verifier queries the RTR for the measurements of Components B and C, the RTR provides these results. If Component A is trusted, then the verifier can trust that Components B and C are also in a secure, expected state, as their hash values match the expected ones.

This process ensures a continuous **chain of trust** throughout the platform, starting from a foundational trusted component and extending to all subsequent elements. Any deviation in expected hash values signals a breach of integrity, indicating a potential compromise.
