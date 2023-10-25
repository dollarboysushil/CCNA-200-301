## Topics  we will cover

- Redundancy in network
- STP (Spanning Tree Protocol) 


## Network Redundancy

- Redundancy is an essential part of a network which makes the network infrastructure resilient to failures as much as possible

![](images/Pasted%20image%2020231025141721.png)

`However without spanning tree, there is a major problem here whcih can destroy the network`


## Broadcast Storms

![](images/Pasted%20image%2020231025142831.png)

![](images/Pasted%20image%2020231025142848.png)

![](images/Pasted%20image%2020231025142857.png)

`although pc2 recived the arp request and sent its reply, broadcast frame still remains in the network switches will continue flooding them `

- These broadcast frames will loop around the network indefinitely. If enough of these looped broadcasts accumulates in the network, the network will be too congested for legitimate traffic to use the network. This is called a `Broadcast strom`

- Each time a frame arrives on a switch port, the switch uses the mac address field to 'learn' and update its mac address table. When frames with the same source mac address repeatedly arrive on different interfaces, the switch is continuously updating the interface in its mac address table. This is known as `Mac Address Flapping`

![](images/Pasted%20image%2020231025143607.png)


## STP (Spanning Tree Protocol)

- IEEE 802.1D
- Switches from all vendors run STP by default
- STP prevents layer 2 loop by placing redundant ports in a blocking state, essentially disabling the interface
- These interfaces act as backups that can enter a forwarding state if an active (currently forwarding ) interface fails
- Interfaces in forwarding state behave normally. They send and receive all normal traffic.
- Interfaces in blocking state only sends and receive STP messages (called `BPDUs` = Bridge Protocol Data Units)
- STP-enabled switches send/receive `Hello BPDUs` out of all interfaces (once every 2 seconds)
- If a switch receives a `Hello BPDUs` on a n interface, it knows that  interface is connected to another switch (routers, PCs, etc do not use STP , so they do not send `Hello BPDUs`)

![](images/Pasted%20image%2020231025144453.png)


## STP BPDUs, Root Bridge Election

- Switches use one field in the STP `BPDUs`, the `BRIDGE ID` field , to elect a` root bridge `for the network
- The switch with the lowest `Bridge ID` becomes the `root bridge`
- All ports on the `root bridge` are put in a forwarding state, and other switches in the topology must have a path to reach the root bridge. 

![](images/Pasted%20image%2020231025145958.png)
`This is the traditional bridge ID`
![](images/Pasted%20image%2020231025150210.png)
`Here SW1 is the Root Bridge , D = (Designated Ports) means it is in forwarding state`

---
---
`Bridge Priority id UPDATE as;`

![](images/Pasted%20image%2020231025151006.png)


![](images/Pasted%20image%2020231025151242.png)


- When a switch is powered on, it assumes it is the root bridge.
- It will only give up its position if it receives a `superior BPDU (Lower Bridge ID)`
- Once the topology has converged and all switches agree on the root bridge, only the root bridge sends BPDUs.
- Other switches in the network will forward these BPDUs, but will not generate their own original BPDUs.

## Practice Question

![](images/Pasted%20image%2020231025153248.png)
![](images/Pasted%20image%2020231025153311.png)



## Step 2 (Root Port , Root Cost)

- Each remaining switch will select one of its interfaces to be its `root port`. The interface with the lowest `root cost` will be the root port. Root Ports are also in a forwarding state.

![](images/Pasted%20image%2020231025153611.png)


![](images/Pasted%20image%2020231025153755.png)

- The `root cost` is the total cost of the outgoing interfaces along the path to the `root bridge`.

![](images/Pasted%20image%2020231025153933.png)


![](images/Pasted%20image%2020231025154316.png)


![](images/Pasted%20image%2020231025154416.png)

![](images/Pasted%20image%2020231025154932.png)

---
---
## Example

![](images/Pasted%20image%2020231025155013.png)

![](images/Pasted%20image%2020231025155309.png)


## Blocking ports to prevent loops


![](images/Pasted%20image%2020231025155549.png)


---
---
## Conclusion

![](images/Pasted%20image%2020231025155632.png)


## quiz

![](images/Pasted%20image%2020231025160258.png)


