## New Public PKIX Extensions

- **Freshest CRL**
  - Also known as **Delta CRL Distribution Point**.
  - It has the same syntax as the **CRL Distribution Point (CDP)**.
  - This extension can be inserted either in a certificate or in a CRL.
    - It **must not** be present in a **Delta CRL**.
  - It is marked as **non-critical**, as not all systems are capable of processing delta CRLs.
