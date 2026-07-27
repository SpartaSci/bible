# main security principles

## security by design 
> secure by design means that the software has been designed from the foundation to be secure 

**Least Privilege**: an individual, process, or other type of entity should have the *minimum privileges* and resources for *the minimum period* of time required to complete a task

**Separation of Duties**: requires that completion of a specified sensitive activity or access to sensitive object is *dependent* on the satisfaction of a *plurality of conditions*

**Separation of Privileges**: it suggests to break a single privilege among multiple independent subjects so that more than one authorizations are required to perform an action

**Defence in Depth**: it means that multiple layers of protection wherein a subsequent layer will provide protection if a previous layer is breached. The layer must be different because if one has a bug and all the layers are equals, an attacker can use that bug to evade protection in each layer.

**Fail Secure**: it is the contrary of **Fail Safe** which means that in case of failure the policy to adopt is to prefer safety instead of security. *Fail Secure* means that if a failure occurs, the system must adopt all the countermeasures to reach security of the system itself. Obviously, we must choose which approach to follow based on our necessities. If we are an hospital, we must choose fail safe, but if we are a bank and a power failure happens, fail secure is needed otherwise everyone can perform any actions or maybe everyone can enter the bank.

**Complete Mediation**: in complete mediation, *every request* by a subject to access an object in a computer system must *undergo* a valid and effective *authorization procedure*. Complete mediation reduces performance but increases the security. This mediation must not be suspended or become capable of being bypassed, even when the information system is being initialized, undergoing shutdown, being restarted, or is in maintenance mode.

**Least Common Mechanism**: this principle states that a minimum number of protection mechanisms should be common to multiple users, as shared access paths can be sources of unauthorized information exchange. So, the least common mechanism promotes the least possible sharing of common security mechanisms.

**Psychological Acceptability**: more complex the user interface is, more higher is the likelihood for employees to do errors or to use it in a wrong way causing bad behaviours. Psychological acceptability refers to the ease of use and intuitiveness of the user interface that controls and interacts with the cloud access control mechanisms. Users must not interpret complex instructions otherwise it never use these instructions and this can cause a loss of security.

**Weakest Link**: attackers always try to identify the most fragile part of the whole protection system in order to start their activities to destroy/attack the system. So, the security of a system is the security of its weakest link. The security system should be revised again and again to detect and resolve the weakest parts in the security chain because the weakest parts are the first exploited by attackers.





## zero trust
> In Zero Trust approach, all types of relationships or any elements are considered untrusted. No one and nothing is trusted. The security must be distributed and to reach security, microperimeters into the network are created and maintained secure (the same security typically) following zero trust approach. To check security, the process is always active.
> For reaching security, the **Continuous Adaptive Risk and Trust Assessment** must be used. It means that security is a process, so you need always to predict some possible scenarios, prevent them and then, maybe, detect them and respond to them. It is a loop that must be repeated continuously.


## open design

> it means that if you use security through obscurity principle maybe you were successfully attacked, but if you use an open design which is secure for the community, you are secure. Everything that is open, is tested more and more time than something that is closed and never tested enough. For this reason, using an open design for reaching security guarantees more secure even if it is public.

