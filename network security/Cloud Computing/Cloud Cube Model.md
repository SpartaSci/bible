
In 2009, The Jericho Forum group proposed a model called the **Cloud Cube Model** (based on a three-dimensional cube). It was originally created to address the issue of de-perimeterization in networks. The Cloud Cube Model illustrates different permutations available in cloud offerings and presents four criteria to differentiate various types of cloud formations.

The **primary objectives** behind building the Cloud Cube Model were:
- Represent different formations of clouds;
- Highlight their key characteristics;
- Represent the benefits and risks associated;
- Present a roadmap for more detailed study and to make the environment more secure.


The Cloud Cube Model is designed to represent *four security-related criteria* called **dimensions** (each with two possible responses, resulting in 16 different forms of cloud computing environments):

**Data Boundary**: *Where will the data be stored?* The physical storage location of the data can be either **Internal (I)**, within the organization’s physical boundary, or **External (E)**, stored outside. Note: Internal is not necessarily more secure than external; the use of both provides the most secure usage model. Example: Data on virtualized hard disks in an organization’s data center is internal, while data on Google Cloud Storage is external.

**Ownership**: *Will the cloud be formed using proprietary technology or open technology?* This dimension determines the ownership of the technology services and interfaces used for building the cloud. These technologies can be **Proprietary (P)**, meaning the organization providing the service retains ownership, or **Open (O)**, meaning the cloud services are built following published and recognized open standards.

**Security Boundary**: *Will the cloud operate within the organization’s network boundary only, or also outside the boundary?* This third dimension represents the ”architectural mindset”. The security boundary can be:
- **Perimeterized (Per)**: Network boundaries are often indicated by firewalls. This approach enhances security but prevents collaboration because nobody can access anything inside the network perimeter. However, VPNs expand the network boundary while keeping the computing environments perimeterized.
- **De-perimeterized (D-p)**: This system shows the natural intent to collaborate with systems outside its own perimeter (Collaboration Oriented Architecture (COA)). Such systems should be protected using techniques like data-level authentication and encryption.


**Sourcing**: *Will the development and maintenance of the cloud service be outsourced or done by an in-house team?* This dimension indicates who delivers and manages the service. If the service is delivered by a third party, it is called **outsourced**, while if it is provided by the organization’s own/internal team, it is **insourced**. Insourced cloud services indicate [[network/Private Cloud|Private Cloud]], while outsourced services can deliver both [[network/Public Cloud|public]] and [[network/Private Cloud|private]] clouds. Sourcing is basically a business decision that must consider the expertise and reputation of the team that is going to deliver the cloud.
