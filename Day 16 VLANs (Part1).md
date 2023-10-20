
## Things we'll cover
- What is a LAN?
- Broadcast domains
- What is VLAN?
- What is the purpose of VLANs?
- How to Configure VLANs on Cisco Switches?


### Broadcast domains.

Group of devices which will receive a `boradcast frame` (destination mac FFFF.FFFF.FFFF) sent by any one members

![](images/Pasted%20image%2020231020121302.png)

- If pc 6 sends the broadcast frame 
	- switch 3 receives it , it will flood the frame to PC7 , PC8 and R2
	- R2 will not forward the frame

- If R1 sends the broadcast frame
	- it will be received only by R2



### What is a LAN?

Lan is a single broadcast domain , including all the devices in that broadcast domain

`In above figure Green , Blue , Yellow and Orange shows the LAN`


### What is a VLAN?

![](images/Pasted%20image%2020231020125956.png)
`There are three main departments in this office.`
For both security and performance purposes it would be best to split up these into separate subnets
![](images/Pasted%20image%2020231020130215.png)
`lets say pc in engineering department sends broadcst message intended for other pc in the same engineering department . since it is a broadcast message , switch will flood it out of all interfaces. hence problem in both performance and security`


#### Lets Split up into separate subnets

![](images/Pasted%20image%2020231020130611.png)

- If pc1 wants to send traffic to pc 2 then 
	- pc1 forwards frame to the switch
	- switch will send it to R1
	- R1 will forward frame back to the switch
	- switch then forward it to the destination (PC2)

`Here instead of PC1 being able to send traffic directly yo pc2 , we forced it to send traffic through R1, where we can configure certain security policy `

But there is still a problem
- If the frame is Broadcast of Unknown Unicast
	- the switch will flood the frame out of all interfaces
	- ![](images/Pasted%20image%2020231020131119.png)


- Although we separated the three departments into three subnets(layer3) , they are still in the same broadcast domain (layer2). so in case of broadcast frame / unknown unicast frame , the switch will flood the frame out of all interfaces . 
	
- It is because switch is only aware up to layer 2 , Switch looks at Layer 2 info like source and destination mac address only. It doesn't care about layer3,4 etc. 
- Even though there are three subnets there , switch doesn't know about that. PC1 will send frame to the switch , it will see the destination MAC address of all `F` and then flood the frame. Which is bad in terms of performance and Security.
- Hence although we separated the three departments into three subnets meaning they are separated at layer 3 , they are still in the same broadcast domain, the same layer 2 network, or in the same LAN. 

---
---
Although these pc are all in the same lan we can use vlans to separate them at layer 2
![](images/Pasted%20image%2020231020131607.png)

- We configure the switch interface to be in specific VLAN and then the end host connected to that interface id part of that VLAN
![](images/Pasted%20image%2020231020131824.png)
`Here broadcast traffic is forwarded only in same vlan`

- Switch will consider  each VLAN as separate LAN and will not forward traffic between VLANs (including broadcast / unknown unicast traffic)

![](images/Pasted%20image%2020231020131950.png)
`if pc1 want to ping pc2 
`1pc1 -> switch
`switch -> Router
`Router -> switch
`swich -> pc2`


Routers is used to route between VLANs, Switch does not perform inter-VLAN routing. It most send the traffic through the router
Traffic arrives on a VLAN10 interface is forwarded out of VLAN 10  interface `Both in same VLAN`
A switch will never forward traffic directly between two different VLANS


---
---
# Reviews
![](images/Pasted%20image%2020231020132717.png)



---
---
---

### VLAN Configuration

![](images/Pasted%20image%2020231020132835.png)


|SN| **COMMANDS**      | **Description** |
|---| ----------- | ----------- |
|1| show vlan brief      |  Displays the vlan that exist on the switch By default all interfaces are assigned to VLAN1|
|2|interface range g1/0 - 3| Selecting range of interface |
|3| switchport mode access | access port is a switchport which belongs to a single vlan and usually connects to the end hosts |
|||Trunk port= Switch port which carry multiple vlans (more in next day)|
|4|switchport access vlan 10|Assign VLAN to the port|
|5|vlan 10| to enter configure mode of vlan 10 or this command creates vlan if not created|
|6|name Engineering|Assigning the name|

![](images/Pasted%20image%2020231020133706.png)
![](images/Pasted%20image%2020231020133723.png)


