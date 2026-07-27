[[Advanced ISS/PKC/Public Extensions|Public Extensions]]

The second group of extensions is the one conveying additional attributes to the subject and the issuer in the certificate. There are three of them: 

- **Subject Alternative Name**
- **Issuer Alternative Name**
- **Subject Directory Attributes**

Typically, the identification (for both issuer and subject) is performed by the **DN (Distinguished Name)**, which uses a strange syntax, for example:
- C (Country) = IT
- O (Organization) = Politecnico di Torino
- CN (Common Name) = Antonio Lioy
- … and so on


That notation, the one with the syntax “component = value,” is named **Distinguished Name**, and it is a remainder of the X.500 directory because it represents a hierarchy: country, then the organization, and then the individuals, etc. 

It could be possible to have, under the organization, an **Organization Unit (OU)**, like a department inside an organization, which was meaningful for X.500 but is no longer used. For this reason, in the subject name and issuer name, it is compulsory to use that format. So, another place to put the name, which is meaningful for internet applications, is needed.

In the issuer and subject names, which are standard fields in **X.509 v1**, we must use the **Distinguished Name (DN)** or leave it empty. The other place to put names that are meaningful is:

- **Subject Alternative Name (SAN)**: It allows using different formalisms to identify the owner of the certificate, which are meaningful. For example:
  - It is possible to use the email address if the key is owned by an individual.
  - The IP address (or MAC address) if the key is owned by a device.
  - The URL if the key is associated with a procedure that offers a service through that specific URL. 

	In general, it contains the meaningful identifier for the applications. There can be more than one SAN. This is always critical if the field subject-name is empty.
- **Issuer Alternative Name (IAN)**: It allows using different formalisms to identify the CA that issued a certificate or a CRL (e.g., email address, IP address, URL). This is always critical if the field issuer-name is empty. It is less critical than before because the issuer is just the issuer of the certificate, while the application relies on the subject (not on the issuer). 
	\
	You are protecting IP traffic, access to the web, email, or creating a signed document. The same considerations apply to the issuer, but this is seldom used, as there is often no purpose in using this. Below are the alternative names that it is possible to use:

	- **rfc822Name**: This represents an email address (e.g., `lioy@polito.it`).
	- **DNSName**: This is the name of a server (e.g., `www.polito.it`), indicating that the private key is associated with that server.
	- **IPAddress**: Remember that a device can have more than one IP address due to multiple network cards or changes if using DHCP. Thus, using a certificate with an IP address can be risky, as you must ensure that it will always correspond to that node.
	- **Uniform Resource Identifier (URI)**: Used to protect a specific access point to a web-based procedure.
	- **directoryName**: This is used if a different kind of directory is in use, different from X.509.
	- **X400Address**: These are email addresses used in the old OSI system, quite similar to the X.500 notation (e.g., `Country=IT/.../.../...`). However, this kind of address is no longer commonly used.
	- **ediPartyName**: This is interesting for EDI (Electronic Data Interchange), a format used by companies to automatically exchange information about products or parts. For example, a car manufacturer could use EDI to specify an order for tires, allowing for immediate information exchange without the need for physical documentation. Various standards exist, such as **EDIFACT**, used in factories for supply chain needs.
	- **registeredID**: This represents any other kind of official identifier (e.g., DUNS, which is a unique identifier for companies worldwide).
	- **otherName**: This is the escape option. If none of the above is suitable, you can define something under `otherName`, which must include an OID (Object Identifier) plus a value. The OID defines your own alternative name, and then you provide the corresponding value.
- **Subject Directory Attributes**: In addition to names that are identifiers of the entity controlling the private key, it is possible to include some directory attributes associated with the owner of the certificate. 
	\
  The Subject Directory Attributes allow for the storage of directory attributes associated with the certificate owner. For example, the **Department of Defense (DoD)** in the United States uses this field to store the “citizenship” (e.g., Italian). 
\
  The actual usage of this extension heavily depends on the application, as no standard definitions exist, making it seldom used. It is public because it is in the standard, but the possible values are application-defined, so it is normally used only in a very closed environment. 

  It is considered **non-critical**.
