# Development Processes

## Overview of Security Assessment

Security assessment is not solely conducted at the end of development; rather, it is an ongoing activity throughout the development process of a product. This approach is crucial because the cost of fixing defects increases as we progress through the development stages. According to a study by NIST, the cost associated with fixing bugs is as follows:

- **Early Development**: If bugs are found early in the development process, the cost is **1x**.
- **Coding/Testing**: Fixing the same bug during coding/testing increases the cost to **5x**.
- **Later Stages**: As development continues, costs can escalate even further.
![[SVT/roba inutile/_image/dev_cost.png]]
## Typical Phases of Software Development

The typical phases of software development are as follows:

1. **Informal Requirements**: Initial ideas and concepts in the developer's mind.
2. **Requirements Specification**: Detailed analysis and formal documentation of requirements.
3. **Design**: Creation of design specifications based on requirements.
4. **Implementation**: Coding and building the actual product.


From a security perspective, each phase plays a crucial role:

- **Requirements Specification**: Establishes the security policies.
- **Requirements Analysis and Specification**: Known as **risk assessment**.
- **Design**: Focuses on **security design**.
- **Implementation**: Involves implementing **security controls**.
- **Operation**: Includes setting up and managing security.



Each phase introduces potential vulnerabilities. Instead of only performing assessments during the final implementation, assessments can be conducted in the early stages of development. 

### Types of Assessments

Two primary types of assessments can be performed:

1. **Validation**: 
   - A comparison between the current phase of development and the user's expectations.
   
2. **Verification**: 
   - A more formal activity that involves:
     - Comparing two different products of development.
     - Conducting an internal consistency check of one product.
     - For instance:
       - In the **requirements specification** phase, verification checks for internal consistency (ensuring no contradictions).
       - In the **design** phase, verification ensures that the design accurately implements the specified requirements.
