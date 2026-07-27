# Application Firewall
An application firewall is a firewall that controls input/output or system calls of an application or service.

For example:
> An application firewall can determine if an email message contains a type of attachment that the organization does not permit (such as an executable file), or if instant messaging (IM) is being used over port 80 (typically used for HTTP).


Another feature is that it can block connections over which specific actions are being performed (e.g., users could be prevented from using the FTP “put” command, which allows users to write files to the FTP server).

This feature can also be used to allow or deny web pages that contain particular types of active content, such as Java or ActiveX, or that have SSL certificates signed by a particular certificate authority (CA), such as a compromised or revoked CA.

## Web Application Firewall
A web application firewall (WAF) is an application firewall that monitors, filters and blocks Hypertext Transfer Protocol (HTTP) traffic as it travels to and from a website or web application. 

Generally, these rules cover common Web Application attacks such as Cross-site Scripting (XSS) and SQL Injection.


### Example

**WAF**

AWS offers a **WAF (Web Application Firewall)** that lets you monitore the HTTP and HTTPS requests that are forwarded to an Amazon API Gateway or to an Amazon CloudFront or to an Application Load Balancer. This WAF helps to block common attack such as SQL injection, Cross-site scripting, HTTP flooding (type of DoS attack) and ”Scan and Probes”. 

- The WAF can be configured in different ways, using different policies for allowing traffic to pass through. The different policies can be:
	- IP Match Condition
	- Geo Match Condition
	- String Match Condition,
	- Regex Condition
	- SQL Injection Match condition
	- Size constraint conditions 
	- Cross-site scripting match conditions.

- Another important aspect is that the AWS WAF doesn’t support the priority of the rules (priority can lead to conflict anomalies) and allows only denylist or allowlist approach (these avoid the conflict anomalies).




**Modsecurity** is an open-source closs-platform web application firewall. 
A main feature of Modsecurity is that it support configuration based on Open Wordwide Application Security Project rules. 