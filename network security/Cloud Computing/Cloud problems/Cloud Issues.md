[[cybersec/_problem/issue|issue]]

> A security issue is something happening in any assets attacks, misconfiguration, fault, damage, loopholes, and weakness in the system. Obviously, in the cloud, the system is more complex because there are more many aspects to consider.


The most important cloud security issues are related to:

## Storage and Computing
data is a vital part of cloud computing. Customers are often averse to putting their data in the hands of a third-party storage service provider for fear that the data could be tampered with or used without permission. For customers is important that their data are consistent during computation, confidential at every stage of processing and perpetually stored to update the records.

The main issue of **data storage** is the loss of control of data, called **data breach**. It is hard to detect a data breach because the cloud computing model doesn’t provide full control over the data (un-trusted computing) and it is harder to check data integrity and confidentiality. Moreover some cloud storage providers can store data data through the ”multi-location” approach around the world; this can cause different problems related to security threats and legal problems because each location can have different policies.

Moreover, it is needed that cloud services are always running and available because data or services must be usable at each moment (**data and service availability**). To guarantee data and service availability, providers adopted a *multi-tier architecture*, made at the application and infrastructural levels, to add high availability and scalability. This approach allows to avoid DoS attacks because software and hardware failure measures can be built in all tiers. Another issue in terms of availability can be related to hardware availability. A single glitch can lead to partial or complete blackouts that can last minutes or hours. For this reason, during the negotiation of the [[network security/Cloud Computing/SLA - Service-Level Agreements|SLAs]], disaster *recovery and backup plans* should be negotiated to avoid bad effects when one of these issues happens.

To provide service and data availability, the **cryptographic mechanisms** are the most security measures applied. These mechanisms can be well designed because otherwise some attacks can be easily done (e.g. brute-force attack). The mechanisms to use should be chosen according to the CPU and GPU in the infrastructure. Moreover, another data-related problem may be data recycling due to the wrong way of deleting data.
 
When *data need to be deleted*, they should sanitizated before. **Data sanitization** is the process of cleaning or removing certain pieces of data from a resource after it becomes available for other parties. This process is necessary before that data and physical resources are sent to the garbage. Deficient implementation of data destruction policies at the end of a life-cycle, may result in data loss and data disclosure, because hard disks, for example, might be discarded without being completely deleted. Especially in cloud services where resources allocated to one user will be reallocated to a different user at a later time, the data sanitization process is assuming a fundamental role.

The advance threat report says that **malware** is active and perform actions in every 3 min at a single organization on average. The main problem behind that is, if one system contains malware then due to inheritance the *malware can spread across the cloud* or malware spreads to all the device which are synchronized with the file it attaches to


## Virtualization
the multi-tenancy and virtualization concept is not free from threats and attacks. 

The first issue can be related to the **VMs image management** because the nature of the cloud allows the provider to create, modify and copy VM images. Several research works provided studies on security risks for an image repository, from the perspective of the **repository administrator**, the **cloud provider** and the **cloud user**.


- The **administrator risks** are *hosting and distributing malicious images*:
	- **Theft and Code injection**: images have to be kept in a repository which, even at an offline state, are vulnerable to theft and malicious code injection. One possible solution to avoid VM theft is to concatenate several images because it is harder to copy large-sized files combined than one only.
	- **Unknown vulnerability**: an unknown vulnerability can be distributed within the VMs at the distribution time. In this case, the vulnerability is not known, so it can be exploited later, when it is discovered.
	- **VM spawl**: the number of VMs is continuously growing, while most of them are idle or never resumed from sleep, which may cause wasting resources and complicate VMs management for the user. It is a sort of DoS attack which should be avoided by the Hypervisor. For example, if some VMs in Crownlabs are not stopped, the hypervisor will stop them otherwise the resources will be wasted doing nothing.
- The **cloud provider risks** *leaking data* if unwittingly publishes images, because images contain fully configured applications and data.
- The **cloud user risks** *running vulnerable, malicious, out-of-date or unlicensed images* stored at an insecure, wrongly administrated repository.


### other issues

VMM -> Another type of attack, related to the VM Monitor/Manager (VMM), is called [[cybersec/attacks/Hyperjacking|Hyperjacking]] which means that the control of VMM or hypervisor is under the attacker. The attacker can monitor other virtual machines, access the shared infrastructure, monitor the CPU utilization or can bring the VMM shutting down.


Mobility -> VMs can be easily copied or moved to other servers (VM cloning or template image cloning).
The main issues are:
- **Network attack on VMs migration**: during the migration, a MITM can perform some actions such as copying the VM, modifying it and so on.
- **Redundancy of erroneous configurations**: many virtual machines may run the same image, which may contain incorrect configurations or bugs.
- **Proprietary information disclosure**: a template image might retain data from the original owner (e.g., secret keys and cryptographic salt values) that should be removed before migrating.

[[network/IaaS|IaaS]] -> Another issue related to the VMs in the IaaS infrastructure is the **VM hopping** which consists of maliciously gaining access to different VMs belonging to other customer by exploring the *VM-to-VM* or *VM-to-VMM* attack vectors. In other words, the attacker use a VM to gain the access to other VMs or to the Hypervisor in order to check the resource usage, to alter the configuration of the system (VM-to-VMM) or to leak sensitive data.

Another issue can be the more dynamic **malware** against the more secure box used by the virtualization (sandboxing technique - a form of isolation in which the VM run in a box and cannot go outside).


# Network
The network security issues in the cloud is to achieve enough security in the dynamic network due to the drastically increase of the network security configurations needed. For example, the firewall didn’t know migration, scaling, new connections and new paths during the dynamic scaling or live migrations.


# Internet and Services
Cloud infrastructures are not only composed by the hardware where the data is stored and processed, but also by the path to where it gets transmitted on Internet.

The main issues related to the TCP/IP model are equal to the main issues for the cloud; moreover, for example, if a cloud provider provides an Application-as-a-Service, the main issues are related to the application level. Moreover, data centers have a massive number of resources in an elastic connected pool that require a proper link bandwidth to support great amounts of network traffic. But, despite the bandwidth, **DoS attack**, in particular DDoS, can be used to make some services unavailable.


There are three types of DDos attacks in a cloud:
- **DDoS attack to the servers**: the server overloads by either *processing a single malicious request* that expects to exploit a vulnerability or *processing a massive number of requests*.
- **DDoS attack to the network**: a network link is fully saturated with bogus requests belonging to the attack and thus reaches its bandwidth capacity, ceasing honest connections.
- **DDoS attack to an intermediate network device**: one or more intermediate network device (e.g. routers, DNS Resolver, Load Balancer, etc.) also become saturated to a large amount of bit rate processing per second.

Moreover, in the cloud computing context, DDoS can be:
- **Direct**: the direct DDoS attacks imply a predetermination of the target service host machine.
- **Indirect**: the indirect DDoS occurs when a DDoS attack against a specific hosted service from a specific machine causes all other services hosted by the same machine to also become unavailable


# Access

In the multi-tenant cloud environment there are a large number of customers. Each customer’s access cloud services using websites or front-end interface that nowadays are an attack door. So, people required some access control mechanisms. The **access control** must be performed also for avoiding unauthorized people to have physical access to data centers. It is needed that the data centers are thought and built as secure and safe places. 

Moreover, having **unauthorized physical access** can be ambitious in terms of profit for attackers because data centers store massive amounts of data of different customers that can be stolen and resold. 

Also the money mules, who are people unaware of the illegality of their actions, can impersonating a customer and instigate a way in for having physical access. **Money mules** are paid convinced that they have done nothing illegal but in case of success and subsequent discovery of the attack, they are the only ones who get into trouble.

Another problem related to the access in cloud environments are the **user credentials** that must be secure and kept secure as well.

The cloud require **authentication** technique to achieve a secure access to cloud applications. A weak authentication mechanisms make cloud attacks, such as brute-force and dictionary attacks, feasible. The cloud providers should provide different authentication technique and credentials recovery.

**Authorization** it is the process of granting or denying permissions to a person or system. In the cloud, the deployment of authorization mechanism for each user and for each data is a complex task. In centralized system instead, the authorization is very easy to handle. With an insufficient or faulty authorization checks, a third party may be accessing the cloud-based services.

**Anonymization** it is a technique of destroying tracks, or the electronic trail, on the data. There are many techniques in the cloud to achieve privacy by using anonymization techniques to ensure that information about cloud customers is kept hidden and is never disclosed in front of any person other than the customers themselves. Nevertheless, there are deanonymization attack, active or passive attack, that can breach user privacy on the basis of user origin knowledge (anonymization data can reveal the identity of the user).


