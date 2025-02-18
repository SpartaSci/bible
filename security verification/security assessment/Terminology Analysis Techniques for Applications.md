

When we talk about techniques for the security assessment of software, these acronyms are usually found:

- **SAST (Static Application Security Testing)**  
  Testing here means something more general, more like what we call verification. It includes real testing and white-box static analysis of source code.  
  **Examples**: PVS Studio, Coverity, FindSecBugs.

- **DAST (Dynamic Application Security Testing)**  
  This is what we typically call testing since it performs black-box dynamic analysis (vulnerability scans).  
  **Examples**: OWASP ZAP, Acunetix.

- **IAST (Interactive Application Security Testing)**  
  This technique is a sort of halfway between static and dynamic. It is more properly a dynamic technique since it runs the software, but there is a significant static analysis component included.  
  **Examples**: Acusensor, Contrast Assess, Glass Box Appscan.

## SAST vs DAST

In the static approach, it is possible to find more vulnerabilities, but also more false positives compared to DAST (since DAST observes a running system). Static analysis is typically more conservative, often yielding more false positives than similar tools used for classic analysis (e.g., functional errors). 

Other differences include:

- **Development Stages**:  
  DAST can only be used in the later stages of development, while SAST can be utilized throughout all stages. 

- **Information Provided**:  
  SAST provides more information about vulnerabilities, including the specific line of code where the vulnerability exists, which is not possible with DAST. 

- **Libraries**:  
  A challenge for SAST is that libraries often do not provide source code. SAST analyzes source code and is applicable only to some languages, while DAST is independent of source code.

- **Complexity**:  
  SAST employs sophisticated algorithms and may require more time to perform analysis.

## IAST

IAST is a relatively recent concept that tries to combine static and dynamic analyses. It was introduced because modern software applications, especially web apps, are quite complex and composed of many third-party components (which pose issues for SAST). The main ideas include:

- An agent provided by the tool is added to the running system and operates within a running application (code instrumentation, meaning that we do not run the deployed code but the one with this agent).
- The agent has access to code and all execution details, but only the triggered code is analyzed.
- While examining the running code, the agent can perform static analysis.
- The agent can run continuously (even during operation).
- Reports are live and continuously generated/updated.

### Pros and Cons of IAST Tools

**Pros**:  
- IAST tools can find many vulnerabilities (like SAST) while avoiding some false positives reported by SAST.
- They are also very fast and scalable, making them suitable for DevSecOps.

**Cons**:  
- These tools are not yet available for all languages/frameworks.
- They are not yet widely known or adopted.
