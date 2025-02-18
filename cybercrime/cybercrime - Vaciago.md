
# definitions

[[cybercrime/definitions/digital evidence|digital evidence]]
- invisible
- need to be interpreted
- require attention since can be altered 
- legal requirements:
	- admissible
	- authentic
	- reliable 
	- proportional
- created by human or computer or both




[[cybercrime/definitions/Digital Forensics|Digital Forensics]]:
- data coping -> hashing -> analysis
- principles:
	- data integrity
	- chain of custody
	- specialist support 
	- appropriate training
	- legality
- investigation process:
	- [[cybercrime/investigation/Identify the Suspect|Identify the Suspect]]
		- IP and data retention
		- [[computer forensics/definitions/osint|osint]]
		- SOCMINT
	- [[cybercrime/investigation/Detecting and Seizing Digital Evidence|Detecting and Seizing Digital Evidence]] 
		- bit stream copy
		- hashing -> digital fingerprint
	- [[cybercrime/investigation/Validating Digital Evidence|Validating Digital Evidence]]
		- ad hoc tools admissible in court
	- [[cybercrime/investigation/Chain of Custody|Chain of Custody]]
		- documented and unbroken process of handling evidence
	- [[cybercrime/investigation/Analysis of Digital Evidence|Analysis of Digital Evidence]]
		- static -> on a bit stream copy 
			- re-analysis
			- presence of counterpart is needed 
		- live 
			- for encrypted system
			- network analysis
		- methods
			- text search
			- image search
			- data recovery
			- data carving
			- metadata recovery
		- open or closet sources tools
		
	- [[cybercrime/investigation/Presentation in Court|Presentation in Court]]



Mandatory key disclosure
- depend on the country
- not work because:
	- technical reason (expert can always hide)
	- Human right -> innocent until proved guilty
-> remote forensic, ram, key encryption 


**jurisdiction** about [[computer forensics/Esame - riepilogo con parole chiave#cloud forensics|cloud]] services:
- territorial principle (where data is located)
- nationality principle (nationality of the criminal)
- flag principle (ship,air,space flag state)
- **Power of disposal** (who control data)

**privacy issues** about cloud services:
- lack of control
	- lack of availability
	- lack of integrity
	- lack of confidentiality
	- lack of isolation
	- lack of information on processing (absence of transparency)
	- lack of intervenability




# Budapest convention

- 2001
- Russia has rejected (sovereignity)
- goal
	- criminalize various offences
- criticism
	- human rights, press freedom, data privacy
- first protocol -> racist and xenophobic material
- second protocol -> enhance **international cooperation**

international cooperation
- widest extent possible, is not a recommendation but a requirement
- normal procedure are slow -> **expedited means of communication Art 32**
- share information voluntary
- outlines specific **procedural power** to store data secure
- limit 
	- extradiction
	- real time collection (according with domestic law)
- 24/7 network from every parties (availability)


Uniform legal definitions:
- forgery: intentionally input, change, delete, or suppress computer data to create false information
- fraud: cause financial loss to someone else through altering, deleting, or interfering with computer data or system

procedural powers for law enforcement:
- **Article 32** parties, without authorisation of another Party, can 
	- a) access open source 
	- b) access or receive (through a computer) stored data located in another party, with just the voluntary consent of the person 
- Scope of Procedural Provisions (Article 14): Powers, procedures, electronic evidence, all offenses using computer systems.
- Conditions and Safeguards (Article 15): Human rights protection, judicial supervision, proportionality.
- **Expedited Preservation of Stored Data (Article 16)**: Rapid data preservation, 90-day retention, extendable.
- **Expedited Preservation and Disclosure of Traffic Data (Article 17)**: Traffic data, rapid disclosure, multiple service providers.
- **Production Order (Article 18)**: Data submission, subscriber information, service providers.
	- **Subscriber Information (Article 18)**: Identity, address, billing, service details.
- **Search and Seizure of Stored Computer Data (Article 19)**: Computer system access, data storage access.
- **Real-time Collection of Traffic Data (Article 20)**: Traffic data monitoring, service provider assistance.
- **Interception of Content Data (Article 21)**: Communication interception, serious offenses.
- **Mutual Assistance (Article 25)**: International cooperation, electronic evidence sharing.
- **Expedited Preservation of Stored Computer Data (Article 29)**: Cross-border data preservation, international requests.
- **Expedited Disclosure of Preserved Traffic Data (Article 30)**: Service provider identification, data path tracing.


## italian law n.48/2008

corporate liability:
- companies are accountable for crimes committed in their interest
- top management positions
- and those under their control or supervision
- also foreign company that commit crime in italy
- company must provide evidence employee acted independently

provisions:
- internal cooperation: **ISP retain and protect traffic data** (metadata) up to 90 days (extendable to six months) 
	- service provider have a key role
- competence for investigation and prosecutions
- email seizure
- **best practise**
	- acquiring evidence
	- ensuring authentication of evidence and digital copies
	- emphasized the importance of repeatability
	- impartiality in technical analysis
- changes to the code of **Criminal Procedure**
	- digital inspection and search
	- preservation orders

**standardization of digital evidence procedures**
- unified approach to acquiring preserving and presenting digital evidence in court
- ensuring **integrity and authenticity** become priority

**increased responsibility of judges and legal professionals**


# UN resolution

supported by Russia and other Not in the Budapest convention
include input from a wider range of nations

key aspects:
- international cooperation and standard **harmonization**
- Balancing National Interest
- Human rights and privacy concerns
- emerging threats and supply chain security
- future legal framework for cybersecurity

**ad-hoc committee**

raise legal issues:
- cyber sovereignty and legal boundaries
- public(government)-private(company) cooperation and Liability




compatible with article 22 of Budapest :
- territorial jurisdiction
- extended jurisdiction
	- against their nationals
	- by their nationals
	- outside the state but intended to affect it
	- against the state itself
- key point
	- **coordination among states**
		- authorities must consult and coordinate their actions
	- **compatible with international law**





# IoT

- investigating a **past** crime
	- Keycrime
	- verify alibis
	- track movement 
	- establishing timeline
	- use logs, gps, healt data
- observing an **ongoing** crime
	- FaceFirst
	- surveillance camera
	- body camera 
	- smart sensor
- predicting and preventing **future** crime
	- PredPol
	- crime statistic
	- pattern
	- identify high risk area
	- concern about bias, fairness, data privacy


# cyber crime

falsification -> alteration

computer damage -> availability

unauthorized access -> confidentiality


frameworks to mitigate require management of:
- Access to IT Systems
- Physical and Environmental Security
- Online Transactions
- Cybersecurity Aspects of Electronic Documents with Evidentiary Value
- IT System Monitoring and Periodic Verification