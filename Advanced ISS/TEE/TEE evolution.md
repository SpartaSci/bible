## Open Mobile Terminal Platform (OMTP) and Early Developments

- In **2006**, the Open Mobile Terminal Platform (now within GSMA) introduced the **TR0 specifications**, setting the initial security requirements.
- By **2008**, **TR1 specifications** were introduced, establishing a Trusted Execution Environment (TEE) on top of the TR0 foundation.

## GlobalPlatform and Standardization

- **2010** saw the launch of **GlobalPlatform**, which became the de-facto standardization body for defining TEE interfaces and certifications. GlobalPlatform plays a crucial role in shaping the TEE landscape by setting industry standards.

## Trustonic and Industry Collaboration (2012)

- In **2012**, **ARM**, **Gemalto**, and **G+D** (Giesecke+Devrient) formed **Trustonic** to create an open TEE. These companies, major players in the manufacturing of chips for smart cards and SIMs, specialized in high-security chips with limited functionalities. 
  - Their goal was to make TEE software development **hardware-independent**. Before this, specific TEEs were required for each product, depending on which company had designed it.

- During the same period, **GlobalPlatform** and the **Trusted Computing Group (TCG)** founded a joint working group. This collaboration focused on TEE specifications and their integration with the **Trusted Platform Module (TPM)**.
  - The **TPM** is now compulsory on devices running **Windows 11**.

## Early Business Use Case: Netflix and TEE

The first major business case for TEE emerged with **Netflix**. To ensure security for High Resolution (HR) streaming on smartphones and tablets, Netflix needed to prevent other applications from illegally recording audio and video. By running the **Netflix Trusted Application** within a TEE, they could ensure it had sole control over the screen, audio devices, network data stream, and other relevant resources, preventing unauthorized copying of their content.

## Expansion to Other Industries

Following the Netflix case, TEEs began being adopted in industries like **finance**, **enterprise**, **government**, **automotive**, and **IoT**. In particular, **devices with limited computational capabilities** (like IoT devices) benefit from the high security that a TEE can provide, making it an essential component for secure operations.
