---
tags:
  - network
  - mobile
---
With **active mobility**, the network tracks the user position cell by cell

The *mobility procedure* is named **handover**

The process is completely controlled by the network that adapts routing and commands the [[wireless/WWAN - mobile/_common/UE - User Equipment|UE]] to switch to the new cell

# steps

1. **Neighbour Cell Monitoring**: the network continuously *monitoring* the *signal strength* and quality of neighbouring cells surrounding the Mobile Station ([[wireless/WWAN - mobile/_common/UE - User Equipment|MS]]) current cell. The measurements are sent to the [[wireless/WWAN - mobile/GSM/RAN/BTS - BS - base (transceiver) stations|BS]] every 480ms (in GSM)
2. **Threshold-Based Decision**: The network initiates the handover process if the *signal quality* in the current cell *drops* below a certain **threshold**; Or if a *neighbouring cell's* signal becomes *stronger* and  exceeds a predefined **threshold**
3. **Handover Request**: the network send a *handover request* to the [[wireless/WWAN - mobile/_common/UE - User Equipment|MS]] via the Base Transceiver Station ([[wireless/WWAN - mobile/GSM/RAN/BTS - BS - base (transceiver) stations|BTS]]) currently serving the MS
4. **Immediate Assignment**: the [[wireless/WWAN - mobile/_common/UE - User Equipment|MS]] receives the handover request and prepare to switch to the new cell. The network sends an immediate assignment instructing the MS to tune to the new frequency 
5. **Handover execution**: the MS tunes to the new frequency and time-slot in the target cell
6. **Data and voice transfer**: once the MS is successfully handed over the new cell, *data and voice traffic* are transferred to the new cell
7. **Handover confirmation**: after the handover is completed, the MS sends a *handover confirmation*
8. **Resource Release**: the resources allocated in the old cell for the call are released once the handover is confirmed
9. **Re-Establishment of Connections**: if the handover process results in a change in the [[wireless/WWAN - mobile/GSM/CN/MSC - mobile switching center|MSC]], new connections are established with the new controllers.