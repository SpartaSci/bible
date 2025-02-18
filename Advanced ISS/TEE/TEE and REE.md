
In computers and mobile devices, there are typically two environments: one that is **trusted** (the **Trusted Execution Environment** or TEE) and one that is **normal** or even **untrusted**, known as the **Rich Execution Environment** (REE).

### Rich Execution Environment (REE)

The **REE** is "rich" in the sense that users have freedom to perform a wide range of activities. This includes installing apps and running programs, with the understanding that it is the user's responsibility to ensure the security of what they execute. For example, installing malware in this environment is possible but will not affect the TEE, as the two environments are isolated.

### Trusted Execution Environment (TEE)

Applications that require strong security—such as payment apps, streaming services with **Digital Rights Management (DRM)** (e.g., Netflix), and corporate applications (e.g., a VPN for secure access to a company network)—are run within the **TEE**. The TEE provides an isolated space where sensitive operations can occur securely, separated from the potentially vulnerable REE.

#### TEE Components

The TEE is composed of several **trusted components** that help it operate securely:

- **TEE Communication Agent**: This component facilitates communication between the REE and the TEE. For instance, networking might be performed in the REE, but the data is securely passed to the TEE via the Communication Agent.
  
- **Trusted Drivers**: These are the only components that have access to **hardware secure resources**, such as:
  - **Hardware (HW) keys**, including asymmetric key pairs.
  - **Trusted User Interface (TUI) peripherals** like the screen and keyboard.
    - For example, when entering a PIN to unlock a device, **trusted drivers** ensure that no other applications can read the input. These drivers take control of the peripherals during sensitive operations, denying access to any other apps, and release control once the operation is complete.

- **Trusted Core Framework**: This forms the core of the TEE, ensuring the correct execution of its functions. 


![immagine tee and ree](https://www.accourt.com/wp-content/uploads/2015/07/Architecture-of-the-TEE.jpg)


### TEE Organization

While this framework provides a relatively simple view of the TEE, real-world implementations may vary. Different TEEs may be organized differently depending on the specific system architecture or the security needs of the device.

