


[[cybercrime/definitions/digital evidence|digital evidence]] requires:
- interpretation
- attention
- knowledge

[[computer forensics/definitions/chain of custody|chain of custody]]
- data acquisition
- hashing
- [[computer forensics/tools/write blocker|write blocker]]
- forensic image (dd or [[computer forensics/tools/FTK-Imager|FTK-Imager]]) (copies also [[computer forensics/definitions/slack space|slack space]])

# investigation phase


1. **identification** of [[computer forensics/definitions/digital evidence|digital evidence]] 
	- source can be: [[#memory (RAM) forensics|memory RAM]], [[#file system forensic|hard drives]], [[#cloud forensics|cloud storage]], [[#network forensics|network traffic]], removable media, smartphone, IoT
	- Using [[computer forensics/definitions/osint|osint]] 
2. **collection**
	- *isolate* devices to prevent remote tampering (faraday, network isolation, firewall rules, [[computer forensics/tools/write blocker|write blocker]])
	- *document* everything (photos, serial numbers, device states, running screen)
	- prepare for acquisition
	- *ensure integrity*
3. **acquisition**
	- creating a forensic copy (bit-by-bit) 
	- maintain [[computer forensics/definitions/chain of custody|chain of custody]] 
	- ensure **integrity** with hash
		- **static** (powered down, [[computer forensics/tools/write blocker|write blocker]], pre/post verification hash) [[#file system forensic]]
		- **live** capture RAM [[#OS forensics]], active processes, network traffic [[#network forensics]]

4. **evaluation**
	- check integrity, authenticity, admissibility of the [[computer forensics/definitions/digital evidence|digital evidence]]
5. **presentation**




# non-trusted environment

- node infection
	- trojan horses
	- phishing
	- physical access
	- backdoor
	- persistent unauthorized access
	- spyware
	- ransomware
- network injection (man-in-the-\*)
	- middle
	- browser
	- cloud
	- mobile
	- disk
	- memory
	- side
	- end
- supply chain attacks/infections
	- a single compromised actor is a problem
		- attack the infrastructure while updating it **solarWind Orion Attack**
		- attack libraries and dependencies **heartbleed bug**
		- modify hardware during manufacturing
		- compromise service, hardware, third part
- manipulation from the system owner
	- installing modified application
	- installing different drivers
	- modifying system calss

## APT

- advanced
	- sophisticated techniques against specific victim
		- customized malware
		- exploit zero-day vulnerabilities
		- adopt evasion strategies
- persistent
	- infect for long period by using **low-profile** operations
- threat 
	- specific goal, spying or collecting data


apt schema:
- initial intrusion
	- look for vulnerabilities
	- gather information without direct communication
	- gather information with direct communication (nmap)
- foothold establishment
	- gather persistent access point
	- backdoor
	- malware
- privilege escalation
	- stealing credentials
	- exploiting vulnerabilities
- lateral movement
	- stealing credentials
	- exploiting vulnerabilities
- goal achievement


## APT28
- spear phishing (carefully crafted email)
	- using URL-shortening services
	- weaponized files
- keyloggers for credentials stealing
- malware obfuscation
- time-stomping
- encrypted communication
- lateral movement and privilege escalation
- GOAL: data exfiltration
- or: data desctuction (data wiping)


# lab setup
- secure facility (location and physical security)
	- geographical location
	- defence in depth (authorized people, biometric access, keycard, video surveillance, alarm)
	- air gapped environment
		- faraday cage rooms
		- environmental control (humidity, temperature for devices safety)
- **data protection**
	- network segmentation
		- VLANs and VPN
		- secure communication (encryption)
		- *least-privileged access control*
	- disaster and data recovery
		- verified backup system 
		- verified UPS (uninterruptible power supplies)
	- logging for everything
		- servers, workstations, databases
		- network devices
		- user devices
	- auditing readiness 
		- availability of [[computer forensics/definitions/audit trails|audit trails]]
		- un-tampered (immutable format)
			- WORM storage
		- hashing and/or digital signature
	- policy-based access restrictions
		- separation of duty
- hardware requirements
	- high performance (fast CPU, big RAM and SSDs)
	- forensics servers
		- RAID for integrity, protection against loss, reliability
	- backup servers
	- hardware acceleration using GPU
	- **specific forensic devices**
		- [[computer forensics/tools/write blocker|write blocker]]
		- imaging devices
		- mobile forensics tools
- software
	- flexible and scalable
	- provide safe environments
	- provide easy recovery after failure
	- roaming soul (portable) (portable OS) 
	- virtual machine for safe analysis 
- mount point



# OS forensics 

[[computer forensics/definitions/slack space|slack space]] -> [[computer forensics/tools/FTK-Imager|FTK-Imager]] [[computer forensics/tools/Autopsy|Autopsy]] 
[[computer forensics/definitions/memory dumps|memory dumps]] -> [[computer forensics/tools/LiME|LiME]] -> [[computer forensics/tools/Volatility|Volatility]] [[computer forensics/Rekall]]

metadata -> [[computer forensics/tools/exiftool|exiftool]]

data wiping -> shred

**key areas**
- file system
	- use file system analysis
- registry/configuration files
- system logs
	- Event log analysis
	- source of metadata
- memory dumps
	- memory forensics -> [[computer forensics/definitions/memory dumps|memory dumps]] 
	- [[computer forensics/tools/LiME|LiME]] to capture memory dumps 
	- [[computer forensics/tools/Volatility|Volatility]] and [[computer forensics/Rekall]] to analyse 



## memory (RAM) forensics 



> [!NOTE] Tools for capturing [[computer forensics/definitions/memory dumps|memory dumps]]
> - debugging tools (*gdb*)
> - crash dump utilities
> - **[[computer forensics/tools/LiME|LiME]]**
> - *Fmem* a kernel module that provides a device file for raw physical access
> - *AVML* developed by Microsoft enables the acquisition of volatile memory on Linux systems

> [!NOTE] Tools for analyse [[computer forensics/definitions/memory dumps|memory dumps]]
> - **[[computer forensics/tools/Volatility|Volatility]]**
> - [[computer forensics/Rekall]]

> [!success] allow to
> - recover **volatile data**
> - understand the state of the system 
> - highlight malicious activity
> - perform process analysis
> - **detect code injection**
> - examine registry and **file system**
> - perform **network forensics**
> - recover **credentials**
> - perform crash and failure analysis

> [!danger] challenges
> - size/volume
> - obfuscation
> - forensics soundness (integrity and admissibility)
> - kernel level
 


# file system forensic

- [[computer forensics/definitions/slack space|slack space analysis]]
	- OS does not provide system calls, forensics tools are needed
- **file carving** analyzing [[computer forensics/definitions/cluster|cluster]]
	- recover file from slack space or unallocated areas
- **registry** or **OS config**  analysis


> [!NOTE] Tools
> - stat, istat, debugfs at low level
> - [[computer forensics/tools/FTK-Imager|FTK-Imager]] and [[computer forensics/tools/Autopsy|Autopsy]] at high level


**file**: smallest logical unit from user perspective
- attribute: name, type, protection, location, size


**file system formatting**:

1. erase existing data (full or quick formatting)
2. create partitions (can be formatted independently)
3. select **file system** 
4. create structure:
	- root directory -> FAT or Inode table


**recovery process**

1. analysis of File System Structure
2. use metadata to provide information even if file are deleted
	- timestamp of creation modification and access to build timeline
3. system files and security 

recover deleted Files:
- when file are deleted, OS marks the space as available, but does not erase it, until is overwritten
- forensics tools can search for this file and use file signature
- metadata help augmenting knowledge of files, revealing hidden information, correlating various data





### data sanitization

sanitization wiping shredding

**Data sanitization** ensures that files cannot be recovered after deletion

**File shredder programs** to delete (overwritting) selected files 

**Data Destruction software** to completely erase all data from HDD

write all 0 -> write all 1 -> write random 0/1





# network forensics

> [!NOTE] Tools- 
> - *nmap* to scanning open ports and vulnerable devices
> - *Wireshark* to inspect packet details
> - *xplico* to to breack down application layer
> - *NetworkMiner* to extract files and credentials

> [!caution] challenges
> - encryption
> - obfuscation



1. **evidence identification**:
	- [[computer forensics/definitions/osint|osint]] with social media, email addresses, domain names, IP addresses and public repositories
2. **evidence collection**
	- without altering and preserving integrity 
	- [[computer forensics/definitions/osint|osint]] data can be used
		- archived website snapshot
		- information on registered domain
		- public post 
	- collecting metadata, IP history, timestamp
3. **data preservation**
	- create evidence snapshots
4. **data analysis**
	- look for relationships, patterns and reconstructing timelines  
5. **report**


> [!danger] anti forensics for network forensics
> - encryption
> - tunnelling
> - packet manipulation
> - anti-traffic analysis
> - time-based evasion
> - decoy traffic
> - polymorphic and metamorphic malware
> - anonymization


> [!success] Anti-anti-forensics
> - Deep packet inspection
> - encrypted traffic analysis
> - behavioral analytics
> - comprehensive logging (tamper proof mechanism, [[computer forensics/tools/WORM memory|WORM memory]])
> - threat intelligence integration








# cloud forensics
- distributed environment
- multi-tenancy
- lack of physical access 
- redundancy
- virtualization
- volatility

| Phase     | Lack of Physical Access                | Redundancy                            | Virtualization                           | Volatility                            |
| --------- | -------------------------------------- | ------------------------------------- | ---------------------------------------- | ------------------------------------- |
| **Ident** | Hard to track data/logs, needs CSP     | Excess data, find primary copy        | Locate VMs, hypervisor logs              | Fast-changing data, hard to capture   |
| **Coll**  | CSP API limits, delays                 | Ensure consistency, avoid duplication | Snapshots, exported configs              | Prioritize before loss, live capture  |
| **Acq**   | No physical imaging, trust issues      | Deduplication, metadata check         | VM disks (VMDK, QCOW), snapshots         | Capture before change, automation     |
| **Ana**   | Logical data only, missing metadata    | Compare copies (hashes, timestamps)   | Virtualization-aware tools (FTK, EnCase) | Incomplete data, cross-reference logs |
| **Pres**  | Prove authenticity, CoC, CSP testimony | Explain redundancy’s effect           | Clarify virtualization, use visuals      | Justify gaps, support with logs       |





# Anti-forensics
## Anti-forensics technique
- code obfuscation
- secure file deletion **shredding**
- traffic anonymization
- transaction un-traceability
- tamper-resistant device

## Anti-forensics goal 
- **Data protection and concealment**
	- encryption
	- data wiping *shred*
	- steganography  *StegHide*
		- transparency
		- original data indipendent
		- robustness
		- security
- **evasion and misattribution**
	- timestamp and metadata alteration [[computer forensics/tools/exiftool|exiftool]] 
	- log file counterfeiting 
	- False flag traces
	- deepfakes 
- **disruption of forensics processes**
	- code obfuscation 
	- data compression 
	- malware injection 
- **privacy preservation**
	- proxies and VPN
	- Tor




