
[[cybersec/_problem/threat|threat]]


>A threat in the cloud is a potential event that may be malicious or incidental, compromising cloud resources. 

There can be different threats:
1. **Different service delivery/receiving models**: As servers, storage, and applications can be provided by off-site external service providers, organizations need to evaluate the *risks associated with the loss of control over the infrastructure*. Moreover, data traversing geographical boundaries is subject to different federal laws, which must be taken into account to create correct security measures (e.g., reliable end-to-end encryption or a trust management scheme).
2. **Abuse and nefarious use of the cloud**: Cloud computing provides several utilities, including bandwidth and storage capacities, that can be used improperly (e.g., using bandwidth to perform a DoS attack, or using storage for illegal videos or images). Typically, this happens when a malicious user exploits the free trial offered by a provider. To avoid this, stronger authentication can be used, along with monitoring user-generated traffic by the provider.
3. **Insecure interfaces and APIs**: Cloud providers often publish a set of interfaces and APIs to allow their customers to design interfaces for interacting with cloud services. These can add complexity that may lead to improper use.
4. **Malicious insiders**: Some potential attackers can be internal to the company. In this case, the right level of access is needed (least privilege).
5. **Shared technology issues in a multi-tenancy environment**: In a multi-tenant architecture, virtualization is used to offer shared on-demand services. Vulnerabilities in a hypervisor allow a malicious user to gain access to and control of legitimate users’ virtual machines. Implementing [[network security/Cloud Computing/SLA - Service-Level Agreements|SLAs]] for patching, strong authentication, and access control to administrative tasks are some solutions to address this issue.
6. **Data loss and leakage**: Due to the dynamic and shared nature of the cloud, *data may be compromised or stolen* in many ways. Solutions include securing APIs, ensuring data integrity, secure storage for keys, and regular data backups.
7. **Service/account hijacking**: Service hijacking involves *redirecting the client* (through fraud, phishing, or software vulnerabilities) to a harmful website. Mitigation strategies include security policies, strong authentication, and activity monitoring. Additionally, credentials must be kept secure to prevent issues.
8. **Risk profiling**: Cloud offerings make organizations less involved with the ownership and maintenance of hardware and software. However, this makes organizations unaware of internal security procedures, security compliance, auditing, etc. To avoid this, cloud providers should disclose partial infrastructure details, logs, and data. There should also be a monitoring and alerting system.
9. **Identity theft**: This form of fraud involves someone pretending to be someone else to access resources or obtain credit and other benefits. This threat can occur due to weak password recovery methods, phishing attacks, key loggers, etc. The solution is to use strong multi-level authentication mechanisms and robust password recovery methods.

