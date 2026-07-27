# Static versus Dynamic Analysis

## Classification of Assessment Techniques

The assessment techniques can be classified into two main categories: **Static Analysis** and **Dynamic Analysis**.

### Static Analysis
- **Definition**: Analyzes the system's documentation, code, etc.
- **Requirements**: 
  - Does not require a running or fully developed system; a partial system is sufficient.
- **Examples**:
  - [[SVT/roba inutile/security assessment/intro - Security Auditing (reviews)|Auditing]]
  - [[SVT/roba inutile/Formal methods/formal verification/formal verification|formal verification]]
- **Cost**: Typically more expensive than dynamic analysis. As a result, the most expensive analyses are usually applied only to selected critical components (the most-critical ones).
- Can achieve better coverage of vulnerabilities, especially when based on [[SVT/roba inutile/Formal methods/_formal methods|formal methods]], which can consider all possible inputs the system may have.

### Dynamic Analysis
- **Definition**: Tests a running instance of the system.
- **Requirements**: 
  - Requires the system to be operational.
- **Examples**:
  - [[SVT/roba inutile/security assessment/dynamic/intro - penetration testing|intro - penetration testing]]
- **Exhaustiveness**:
  - Dynamic analysis is inherently less exhaustive than static analysis because testing is conducted under specific scenarios. Therefore, the level of exhaustiveness is limited.
  - If no vulnerabilities are found during testing, it cannot be concluded that no vulnerabilities exist, as some may be missed due to the selected conditions.
- Limited to the scenarios selected for testing, making it less exhaustive.


