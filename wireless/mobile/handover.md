---
tags:
  - network
  - mobile
---
With active mobility, the network tracks the user position cell by cell

The mobility procedure is named handover

The process is completely controlled by the network that adapts routing and commands the UE to switch to the new cell


1- Neighbour Cell Monitoring: the network continuously **monitoring** the **signal strength** and quality of neighbouring cells surrounding the Mobile Station (MS) current cell. The measurements are sent to the BS every 480ms (in GSM)

2- Threshold-Based Decision: The network initiates the handover process if the **signal quality** in the current cell drops below a certain **threshold**; Or if a **neighbouring cell's** signal becomes **stronger** and  exceeds a predefined **threshold**

3- Handover Request: the network send a **handover request** to the MS vis the Base Transreceiver Station (BTS) currently serving the MS

