

> [!attention] questions colors
> in **red** official questions
> in *yellow* un-official made by me to exercise
> 



# network security

**List the main Computing system threats**
- eavesdropping, fraud, theft, sabotage, external attack

**Can you describe the Zero Trust paradigm?**
- in Zero Trust approach any relationships or elements are considered untrusted. 
	 The security must be distributed, each node must secure is little micro-perimeter. Zero Trust is based on 
	- Verify Explicitly, every access must be fully authenticated, authorized and encrypted
	- use Least privilege access through secure policies 
	- assume breach, design the system so if node is compromised, other are not affected
	 
	For reaching security the Continuous Adaptive Risk and Trust Assessment must be used, meaning that security is a process that must be repeated continuously


**What are the characteristics of the Least Privilege Principle? Provide an example where the least privilege principles is applied and another where it is not.**
- With Least Privilege Principle, an individual, process or other type of entity should have the *minimum privilege*s and resources for the *minimum period* required to complete a task.
  As example we can think to a guest host in a network, connected to a database. If principle is applied, it would have only read-only privilege, if not it would have also write access. If it become compromise all the database is vulnerable



**Describe the characteristics and differences between the principles of the Separation of Duties and the Separation of Privileges. For each principle, provide an example.**

- The first focus on the fact that there are more steps in the process and the other focus on the approval of all components
	- separation of duties requires that completion of a specific sensitive activity or access to sensitive data is dependent on the satisfaction of a plurality of conditions  
		- ad example the process of a transaction, it requires an employee to request it, one to approve it, one to verify it 
	- it suggests to break a single privilege among multiple independent subjects so that more than one authorizations are required to perform an action
		- ad example, for a decrypt a bitcoin wallet, more than one secret key is required



# SDN

*What are the four pillars of SDN?*
- separate the control plane from the data plane, so the routing process is implemented on a external controller that is separated by the data plane, controller creates routing table and distribute them to the SDN switch. 
- simple data plane, data plane has to perform only forwarding based on a match/action paradigm
- centralized control, the control software views the entire network and can control it. The controller can be a logically centralized controller, so physically separated devices can coordinate to create routing table. This is increase scalability, robustness and speed but it is also complex since ensuring Consistency, Availability and Partition tolerance all together is complex
- context-based forwarding was not originally present in SDN but it is now. It implies that the controller can take decision runtime based on the actual traffic. The switch send a packet to the controller where it will determinate how to handle that traffic in that specific moment




# firewall
**Describe the main characteristics and types of Firewalls with the proxy capability.**
- A proxy is a server that acts as intermediary between a client requesting a resource and the server providing it. It can be an Open proxy, that exist in the internet outside our network, or a Reverse proxy, present in our network and it offers load balancing, caching, security (by isolating only authorizes request) and encryption.
	We can have: 
	- Application-level gateway, a proxy that acts as relay of application-level traffic. The gateway ask what resource (name of the remote host) to be accessed. If the client provide a valid User ID and authentication information, contacts the application on the remote host. This provide user-level authentication, filtering, caching and logging but add additional processing 
	- circuit-level gateway, a transparent proxy firewall that works at TCP/UDP levels and blocks the direct TCP/UDP connection to the server, it establish a virtual circuits between client and servere

**What are some security threats that a firewall alone cannot prevent?**
- firewall work in perimeter of a network as single entry point, but if a node in the network is compromise, the network is in danger and the firewall cannot do anything. 

**In a firewall, what happens if more than one rule is triggered? What is the relation of this with Policy Anomalies? (++)**
- when more than one Rule is triggered, the action is chosen based on the resolution strategies, that can be: first/last matching rule, more/least specific takes precedence, allow/deny takes precedence.
	Correct resolution strategies are important to avoid Policy Anomaly. In particular the one of Conflict so where the effects if the triggered rules are opposite.

**What are the main capabilities of a Web Application Firewall? Can you describe the difference between ModSecurity and AWS WAF? (++)**
- A WAF is an application firewall that monitors, filters, and block HTTP traffic as it travels to and from a website or web application. Usually cover common Web App attacks such as cross-site scripting. 
	- AWS WAF is a private solution offered by AWS (amazon) to monitor HTTP(S) requests to Amazon gateway, eepending on the policies different matching condition can be used, based on IP, string, sql injection, size constraint, cross-site scripting, etc.. It does not support priority of the rules and allows only denylist or allowlist (so no conflict). 
	- Modsecurity instead is an opensource cross-pplatform WAF. Its main feautere is that it support configuration based on OWASP rules set. 
	 
	So to highlight the difference, one is open source, offer more customization, but require manual integration with the system, the other is cloud based that offers less customization but offer high scalability and integration in the AWS system 
# VPN

 *List all VPN classification*
 - Intranet or Extranet VPN
 - centralized or distributed connection for *internet access*
 - End-To-End or Site-To-Site or Remote Access VPN
 - Customer or provider *provisioned* VPN
 - Overlay or Peer *Model*
 - Hub or Mesh *topology*
 

**What is the GRE protocol? Can you provide some examples of usage?**
- The Generic Routing Encapsulation protocol is a protocol that aim to encapsulate any protocol (including IP) into IP (so works at layer 3). Header contains some flags indicating presence of optional fields, contain protocol type ID, the payload length, session ID, sequence number, ack number.
	GRE does not provide encryption or other security measures.
	Gre can be used ad example to create a Site-to-Site tunnel to allow two hosts in two different subnets communicates.  


*How the gateway position affect the system?*
- gateway can be positioned inside so the VPN traffic can not be inspected by the firewall and the VPN gateway itself is protected by the firewall.
	Outside it implies that the VPN traffic can be analyse by the firewall.
	Integrated allows to reach maximum flexibility
	Parallel can lead to potential uncontrolled access


# cloud

**Describe the Cloud Cube Model.**
- The Cloud Cube Model illustrates different permutations available in cloud offerings and present four criteria to differentiate various types of cloud formations.
	This four criteria are called dimensions, each with two possible response, resulting in 16 different forms.
	Each dimension, has a specific question to respond: 
	- Data boundary, where will the data be stored? Internal or External the respect to the organization's physical boundary.
	- Ownership, Will the cloud be formed using proprietary or open technology? 
	- Security boundary, Will the cloud provider operate withing the organization's network boundary only or also outside?
			For the first security is achieve by firewall and the second require techniques like data authentication or encyrption
	- Sourcing, will the development and maintenance of the cloud service be outsourced or done by an in-house team? This focus on who is responsible of managing the cloud





**From a Cybersecurity perspective, what are the differences between Insourced and Outsourced Cloud Computing Management?**
- Insourced indicate that an internal team is responsible of the management and security of the Cloud, this provides greater control and visibility over security configurations. It can customize encryption protocol (and manage internally the keys), firewall setting and access control without relying on external providers. Also incident response time are typically faster. WIth it result easier be compliance with regulamentations (like GDPR) since it does not have to relies on third part




**What is the Data Sanitization in Cloud Computing? Why is it important? (++)**
- Data sanitization is the process of cleaning data when deleting them, when a file is deleted, usually the system flag that space as available, but the bits are still there, so is necessary implement policies to correctly erase data to avoid data disclosure, especially in cloud computing where resources are reallocated to different user continuously.


**What is the VM Sprawl issues?**
- VM Sprawl is the problem of a lots of VM that are idle and so are wasting resources that can be used more efficiently. This can lead to a sort of DoS attack that the Hypervisor should avoid



**What are the issues that may happen during a Network VM Migration?**
- during an Network VM migration a MITM can perform some actions such as copying the VM, modifying it but we have also to consider possible issues about data disclosure, the previously used ressources have to be sanitaized  


**Describe the NIST guidelines on Cloud Security**
- The key guidelines include: 
	- carefully plan the security and privacy aspect before implementing them
	- define the Cloud Delivery Model to be used
	- ensure that both cloud resources and cloud-based applications satisfy security and privacy requirements
	- maintain accountability over privacy and security
	Some aspect important aspects are: 
	- Governance, extend and force organizational practise to the system life-cycle, by means of regular audit and proper tools
	- Compliance respect to various type of laws and regulamentations
	- trust about SLAs
	- architecture
	- identity and access management
	- software isolation
	- data protection
	- availability
	- incident response
	


**Can you provide a definition of Security as a Service? Can you describe the difference with respect to a traditional network security middlebox/device?**
- Security as a service is a package of security services offered by a service (cloud) provider that offloads much of the security responsibility from a company to the security service provider.
	SECaaS is on-demand service, and it offer cost efficiency, scalability, fast provisioning respect to a traditional network security device. 


# monitoring


*What are some potential security events that could be logged?*
- Operating system logs, like user login or logout, credentials changes, user state change, services running or stopped, failure
- Network device logs, like traffic going through the firewall or blocked, protocol used
- web server logs, failed user authentication, invalid requests, internal errors

*How the NIST guide log management?*
- NIST recommends some questions to address:
	- Which types of hosts perform logging? (log generation)
	- Which types of hosts transfer logs to a log management infrastructure? (log transmission)
	- How often are logs rotated or archived? How much log storage space is available? (log storage)
	- how often is each type of log data analyzed? (log analysis)



**What is a Security Information and Event Management (SIEM) element and why is it important?**
- SIEM is the process of identifying, gathering, monitoring, analyzing, and reporting security related events and is important extract from a large volume of security events those events that qualify as incidents. 
	SIEM functions involve a first phase of collection of log data and normalization filtering and aggregation, then there is log analysis, using pattern matching, scan detection, threshold detection. And finish with event correlation



**What are the issues and limitation of a IDS?**
- issues of IDS involve false positive and false negative, the first is when IDS mistakenly identifies authorized users as intruders, and the second is when actual intruder are not detected. 
	We can evaluate IDS using two measures:
	- Precision indicates the number of relevant retrieved instances out of the total instances detected
	- Recall(sensitivity) indicates the number of relevant retrieved instances out of the total relevant instances 
