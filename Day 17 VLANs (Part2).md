

## Things we will cover.

- What is a trunk port?
- What is the purpose of trunk ports?
- 802.1Q Encapsulation
- Configure trunk port
- Router on a stick (ROAS)





## What is trunk port?
whereas an access port belongs to a single vlan, trunk ports carry traffic from multiple vlans on a single interface.

## How does SW1 know which VLAN the traffic belongs to?
![](images/Pasted%20image%2020231021161712.png)

Answer is `vlan tagging`.

Switches will `tag` all frames that they send over a trunk link. This allows the receiving switch to know which vlan the frame belongs to

`Trunk ports = Tagged ports`
`Access ports = Untagged ports`

## VLAN Tagging

There are two main trunking protocols : 
- `ISL (Inter-Switch Link)` = This is a old cisco proprietary and currently not in use 
- `IEEE 802.1Q`


![](images/Pasted%20image%2020231021162142.png)

![](images/Pasted%20image%2020231021162153.png)
### dot1q inserts 4byte (32bits ) field between source and type/length field
![](images/Pasted%20image%2020231021162232.png)


## Fields in dot1q tag

![](images/Pasted%20image%2020231021162430.png)

### TPID (Tag Protocol Identifier)
- size = 2bytes (16 bits)
- Always set to a value of 0x8100 which indicates frame is 802.1Q tagged
- Each hexadecimal id 4bits to 4* 4 = 16bits = Total size

## TCI (Tag Control Information)

- ###### PCP (Priority Code Point)
	- 3bits in length
	- used for Cos (class of service), which prioritizes important traffic in congested networks
	
- ##### DEI (Drop Eligible Indicator)
	- 1bit in length
	- used to indicate frames that can be dropped if the network is congested

- ##### VID (VLAN ID)
	- 12bits in length = 4096 total vlans (2^12), range from 0 - 4095
		- Vlans 0 and 4095 are reserved and cant be used
		- therefore the actual range is 1-4094
	- identifies the vlan the frame belongs to



## VLAN Ranges

Range of vlan 1-4094 is divided into tow sections:
- ##### Normal VLANs: 1-1005
- ##### Extended VLANs: 1006-4094



## Native VLAN

- It is 1 by default on all trunk ports but can be manually configured
- Switch does not add an 802.1Q tag on frames in the native vlan
- When a switch receives an untagged frame on a trunk port, it assumes the frame belongs to the native VLAN
- It is very important that the vlan matches
- For security reason it is best to change the native vlan to an unused VLAN 



![](images/Pasted%20image%2020231021165655.png)


## Trunk Configuration

![](images/Pasted%20image%2020231021170101.png)

![](images/Pasted%20image%2020231021170125.png)
![](images/Pasted%20image%2020231021170216.png)

![](images/Pasted%20image%2020231021170245.png)



## Native Vlan Configuration

|SN| **COMMANDS**      | **Description** |
|---| ----------- | ----------- |
|1|Switchport trunk native vlan {vlan id} | change the the vlan|
|2|do show interfaces trunk| |
|3|show vlan brief|shows the access ports assigned to each vlan not the trunk ports that allow each vlan|

![](images/Pasted%20image%2020231021170946.png)



## ROAS (Router on a Stick)

![](images/Pasted%20image%2020231021180601.png)
would look like this
![](images/Pasted%20image%2020231021180549.png)

##### Router Configuration

![](images/Pasted%20image%2020231021180713.png)![](images/Pasted%20image%2020231021180804.png)
![](images/Pasted%20image%2020231021180815.png)


- ROAS is used to route between multiple VLANs using a single interface on the router and switch
- The switch interface is configured as a regular trunk
- We configure the VLAN tag and IP address on each subinterface
- The router will tag frames sent out of each subinterface with the vlan tag configured on the subinterface
![](images/Pasted%20image%2020231021181149.png)