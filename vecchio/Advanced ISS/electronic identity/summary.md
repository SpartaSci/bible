### Electronic Identity - Summary Notes

---

#### Delegated & Federated Authentication
1. **Delegated Authentication**: 
   - Relying Parties (RPs) delegate authentication to an external Authentication Server (AS).
   - AS uses established authentication protocols, returning results as tickets or assertions to RP.
   - **Ticket Transmission**: Direct, indirect, or through references. Each method affects security, speed, and network configurations differently.
   - **Ticket Security Challenges**: Risks include manipulation, interception, replay attacks, and reuse by unintended clients.

2. **Federated Authentication**:
   - Supports cross-domain authentication by establishing trust across domains.
   - **Roles**: Identity Providers (IdPs) and Service Providers (SPs).
   - Example: SAML-based identity federation enables user authentication across services by securely transferring identity assertions.

---

#### Policy-Based Access Control (PBAC) with XACML
1. **XACML (eXtensible Access Control Markup Language)**:
   - XML-based language for defining authorization policies based on user attributes, actions, resources, and environmental conditions.
   - **Policy Enforcement Components**:
     - **Policy Enforcement Point (PEP)**: Controls resource access.
     - **Policy Decision Point (PDP)**: Decides on access based on policy.
     - **Policy Information Point (PIP)**: Provides attribute data.
     - **Policy Administration Point (PAP)**: Manages access policies.

---

#### Security Assertion Markup Language (SAML)
1. **SAML Assertions**:
   - Standard for sharing security information (authentication, authorization, attributes) across systems, especially for Single Sign-On (SSO).
   - **Types of Assertions**:
     - **Authentication**: Confirms the user's identity.
     - **Attribute**: Provides user attributes like role or department.
     - **Authorization Decision**: Grants or denies resource access based on provided criteria.

2. **Single Sign-On (SSO)**:
   - SAML enables SSO across services, such as logging into Google Apps using a corporate IdP.
   - **SSO Flows**: Includes front-channel (push) and back-channel (pull) methods for transferring SAML assertions securely.

---

#### eIDAS - Electronic Identification in the EU
1. **eIDAS Regulation (EU Regulation 910/2014)**:
   - Provides a unified framework for electronic identification, ensuring citizens can access services across EU borders using national e-IDs.
   - **Core Principles**:
     - Mutual recognition of national e-IDs.
     - Cross-border interoperability.
     - Emphasis on security, privacy, and transparency.

2. **Implementation Requirements**:
   - **Technical Specifications**: SAML-based, focusing on secure data exchange and cryptographic standards.
   - **Assurance Levels (LoA)**: Defines three levels of authentication strength—low, substantial, high.

3. **EUDI Wallet (eIDAS 2.0)**:
   - Upcoming "EU Digital Identity Wallet" for storing and verifying identity, attributes, and electronic signatures, fostering self-sovereign identity (SSI) within the EU.

---

#### OpenID Connect (OIDC) and SPID (Italy’s Digital Identity)
1. **OpenID Connect (OIDC)**:
   - Authentication layer over OAuth 2.0, optimized for mobile and web-based applications.
   - Supports JSON Web Tokens (JWT) for handling user claims, making it efficient for mobile identity transactions.

2. **SPID (Sistema Pubblico di Identità Digitale)**:
   - Italy's digital identity system for secure access to public services.
   - SPID levels range from simple passwords to multi-factor authentication, ensuring flexibility in security requirements.

---

This summary simplifies the key concepts of electronic identity systems covered in the document, from foundational authentication models to complex regulatory frameworks for cross-border identity verification in the EU.