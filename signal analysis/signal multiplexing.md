>*Multiplexing* deals with **combining** signals all together, while *multiple access* deals with allowing **multiple users** to access and share a communication medium

Multiplexing -> refer to signals
Multiple Access -> refer to users
The concept behind is the same

# FDM - Frequency Division Multiplexing
**Frequency Division Multiple access FDMA** 

FDM has the following properties:
- each signal is modulated to a **different carrier frequency**
- useful bandwidth of medium exceeds required bandwisth of channel 
- Carrier frequencies separated so signals do not overlap. *Guard bands* are needed
- Channel gets band of the spectrum for the whole time, even if there's no data
- Implemented through carrier demultiply (cosine)



> [!Success] Pro
> - no dynamic coordination needed
> - works also for analog signals

> [!Danger] Contro
> - waster of bandwidth if traffic distributed unevenly, since there is fixed allocation
> - guard spaces are needed


# TDM - Time Division Multiplexing 
**Time Division Multiple Access TDMA**

The **synchronous TDM** presents the following characteristics:
- multiple digital signal are interleaved in time
- time slots are preassing and fixed to sources of data. Allocated even if no data
- Data rate of medium exceeds the data rate of digital signal to be transmitted
- **Channels gets the whole spectrum for a limited amount of time**

> [!Success] Pro
> - only one carrier in the medium at the time
> - throughput high even for many users

> [!Danger] Contro
> - precise synchronization is necessary


## Statistical Time Division Multiplexing
> main difference is that time slots are **dynamically** given based on demand



# CDM - Code Division Multiplexing
**Code division Multiple Access CDMA**
> the main idea is to exploit orthogonality in order to separate signals, since signals that are orthogonal between each other can be separated

It present the following characteristics:
- each channels has **unique code**
- all channels use the same spectrum at the same time 
- implemented using spread spectrum technology
	- each sender is assigned a unique binary code $c_i$
	- binary codes are orthogonal vectors
	- therefore, they can be summed together and separated without interference
	- MUX: sum signals after code modulation
	- DEMUX: performs the scalar product to get the desired signal
- TDM and FDM can be applied 



> [!Success] Pro
> - Bandwidth efficient
> - No coordination and synchronization
> - Good protection against interference



> [!Danger] Contro
> - Lower user data rates 
> - More complex signal regeneration
