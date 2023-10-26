
## Topics we will cover

- STP states/timers
- STP BPDU
- STP optional features
- STP configuration


## Spanning Tree Port States


|STP Port State| Stable / Transitional      | 
|---| ----------- | 
|Blocking | Stable |
|Listening | Transitional|
|Learning | Transitional|
|Forwarding| Stable |


- Root/Designated ports remain stable in a `forwarding` state.
- Non- designated ports remain stable in `Blocking` state.
- In case of new device addition, interface shutdown, hardware failure they may have to change states.
- `Listening and Learning ` are transitional states which are passed through when an interface is activated, or when `Blocking` port must transition to a `Forwarding` state.

## Blocking State

- Non designated ports are in `Blocking State`.
- Interfaces in a `Blocking state` are effectively disabled to prevent loops.
- Interfaces in a `Blocking state` do not send/receive regular network traffic. (if arrived, will be dropped)
-  Interfaces in this state do not learn MAC addresses. (if regular traffic arrives, it will be dropped without adding mac address to the mac address table)
- Interfaces in this state will receive `STP BPDUs` (to be aware to Spanning tree topology and be ready to transition towards forward state if needed.)
- But interfaces in  this state do not forward `STP BPDUs`.



## Listening State

- After the` blocking state`, interfaces with `Designated or Root` role enter `Listening State.`
	- Only `Designated or Root ports ` enter the `Listening state` (`Non designated` ports are always `Blocking`)
- This state is `15 sec` long by default. This is determined by the forward delay timer.
- Interface in this state only forwards/receives STP BPDUs.
- It does not send or receive regular traffic.
- Interfaces in this state do not learn MAC addresses. (if regular traffic arrives, it will be dropped without adding mac address to the mac address table)


## Learning State

- After the listening state, a `Designated or Root` port will enter the `Learning state`
- This state is `15 sec` long by default. This is determined by the forward delay timer.
- Interface in this state only forwards/receives STP BPDUs.
- It does not send or receive regular traffic.
- `BUT` Interfaces in this state do not learn MAC addresses. (if regular traffic arrives, it will be dropped without adding mac address to the mac address table)


## Forwarding State

- `Root and Designated ports ` are in Forwarding State.
- A port in this state operated as normal
	- A port in this state send and receives `BPDUs`
	- It also sends and receives normal traffic.
	- It also learns `mac address` from the frames that arrives and add them to the `Mac address table`



## Summary

![](images/Pasted%20image%2020231026182359.png)

---
---

## Spanning Tree Timers


![](images/Pasted%20image%2020231026182512.png)


## Hello STP Timer

![](images/Pasted%20image%2020231026182635.png)


## Forward  Delay Timer


![](images/Pasted%20image%2020231026182706.png)


## Max Age Timer

![](images/Pasted%20image%2020231026182728.png)

![](images/Pasted%20image%2020231026182947.png)


---
---

## Optional Features

## Portfast

- Can be enabled in an interfaces connected to `end hosts`.
- 

![](images/Pasted%20image%2020231026183211.png)
![](images/Pasted%20image%2020231026183232.png)


## BPDU Guard


![](images/Pasted%20image%2020231026183322.png)

![](images/Pasted%20image%2020231026183330.png)

## Other Features

![](images/Pasted%20image%2020231026183402.png)


---
---

## Configuration

![](images/Pasted%20image%2020231026183449.png)

## Configure the Primary Root Bridge

![](images/Pasted%20image%2020231026183518.png)


## Configure the Secondary Root Bridge

![](images/Pasted%20image%2020231026183606.png)



