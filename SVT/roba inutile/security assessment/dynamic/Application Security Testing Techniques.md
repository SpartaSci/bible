

There are also dynamic analysis techniques for software applications. In this case, there are application security testers, which are tools that perform tests on the software to discover vulnerabilities. They are also called application vulnerability scanners because they analyze an application, similar to scanners for networked systems. These tools require that the app is up and running. 

Two important techniques in this area are:

- **Fuzzing**: This technique generates randomized inputs to try to trigger unexpected software behavior (e.g., crashes or errors). This approach is necessary because traditional testing may not cover many cases that are not inspected. For example, if an input data type is an integer that should be positive, you might typically test it with a positive number, zero, and a negative number. However, the vulnerability could be triggered by a specific negative value, not just any negative number (e.g., -1).

- **Proxies**: These tools act like scanners but emulate man-in-the-middle attacks. They can try to subvert communication between the client and server. For web applications, there is a class of tools called vulnerability scanners specialized in performing this kind of attack on web-based systems.

Other techniques are enabled by debuggers, which offer functionalities useful for vulnerability analysis and exploitation (e.g., during penetration testing). Security testing tools may also use static analysis techniques to find good test inputs (such as symbolic and concolic execution). While fuzzing involves randomizing inputs, sometimes it may be more effective to use static analysis to identify potentially dangerous inputs and focus on those specific cases.
