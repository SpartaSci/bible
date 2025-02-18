# Static Code Analysis

Static code analysis is the static analysis of software code and can be done in both:

- **White-box** => source code 
  - Typically used to support code reviews
- **Black-box** => binaries 
  - E.g., Decompilers

When performing static code analysis, there are different types of analysis typically done by the same analysis tool. Some of these analyses are simple and part of what a compiler does, but instead of providing only warnings and errors, they provide information about security. The types of analysis include:

- **Type Checking**
- **Style Checking**: Some rules about providing good code for different programming languages.
- **Program Understanding and Navigation**: Analyze the code (e.g., navigate from function to its definition).
- **Automated Formal Verification** (based on models):
  - Model checkers
  - Theorem provers
  - Control/Data-Flow Analyzers: Used by normal compilers, e.g., if a variable has not been initialized.
- **Symbolic Execution**: Not a real execution but a sort of forecasting of what can happen when a program is executed.
