# Security assessment 


>**Vulnerability** bug or flaw in design, specification, implementation, configuration of a specific system component


Events:
- Vulnerability is created (creation)
- Vulnerability is discovered (discovery)
- Vulnerability is disclosed (disclosure)
- Exploit is created (exploit)
- Exploit is disclosed (exploit disclosure)
- Patch is created (patch)
- Patch is made available (patch publication)
- Patch has been applied to most of the systems


**CVSS** (common vulnerability scoring system, by FIRST)

*Severity* combination of metrics
- Exploitability metrics
- Impact metrics

> **Security Certification** a formal attestation of some properties or capabilities of a system. Made by a third independent party


Static analysis: more expensive
Dynamic analysis: less exhaustive 

White box Techniques: all info available (source,conf,spec)
Black box Techniques: no info available (as an attacker)


**Security assessment** techniques:
- dynamic (and for network)
	- vulnerability assessment
	- penetration testing
- static
	- code analysis
	- formal verification
	- auditing


> **Formal verification**: static analysis of a *system formal model* (mathematically-based)



> **Security Auditing**: formal meeting aiming to evaluate security, finding vulnerabilities, proposing fixes

manual, white box, various stages, performed by independent auditors


> **Vulnerabilities assessment**: identification and reporting of vulnerabilities in a system

static/dynamic white/gray/black box analysis


>**Penetration testing**: identification of vulnerabilities in a system and attempt to exploit them to assess what an attacker can gain from an attack (black box)

- Pre-Engagement
- Information Gathering
- Threat Modeling
- Vulnerability Analysis
- Exploitation
- Post-Exploitation
- Reporting


Application securtiy testing
SAST vs DAST vs IAST


---

# Security Certification


**Evaluation** based on what assurance techniques have been employed and what results have been obtained

**Certification** based on evidence 



**Security Evaluation Standard** ->  **Common Criteria CC** -> *Common Methodology for Information Technology Security Evaluation*



> [!important] CC Objectives
> permit comparability between the results of independent security evaluations





Target of Evaluation TOE has
- Security Functional Requirements SFRs
- Security Assurance Requirements SARs


TOE Security Functionality **TSF**, parts of TOE for correct enforcement of the SFRs



> **Protection Profile PP** set of security requirements for a category of TOEs

> **Security Target ST** set of security requirements and specifications used as basis for evaluation of an identified TOE



> [!question] **CC Recognition Arrangement CCRA**
>- **Authorizing Nations**: have developed *their own Evaluation Scheme* to accredit laboratories to perform CC evaluations 
>- **Consuming Nations**: don't have their own Evaluation Scheme but want to recognize CC evaluations done by others
>- All Nations signers of the CCRA recognize the results of evaluations done by the Authorizing Nations.








Evaluation Assurance Level EAL




# Formal Methods








