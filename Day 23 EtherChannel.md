
## Topics we'll cover

- What is EtherChannel? What problems does it solve?
- Configuring Layer 2/ Layer 3 EtherChannels



![](images/Pasted%20image%2020231028145911.png)

![](images/Pasted%20image%2020231028150003.png)




## Load Balancing


![](images/Pasted%20image%2020231028145942.png)

![](images/Pasted%20image%2020231028150039.png)

![](images/Pasted%20image%2020231028150111.png)


## Etherchannel Load-balancing verification and Configuration



`show etherchannel load-balance` -> to view the current load balancing method

![](images/Pasted%20image%2020231028150326.png)

`port-channel load-balance src-dst-mac` -> to change the load balancing method

![](images/Pasted%20image%2020231028152444.png)

other load balancing method
![](images/Pasted%20image%2020231028152512.png)


---
----


## Creating etherchannel between two switches


There are three methods of EtherChannel configuration on cisco switches:

- PAgP (Port Aggregation Protocol)
	- Cisco Proprietary Protocol
	- Dynamic Negotiates the creation/maintenance of the EtherChannel.

- LACP (Link Aggregation Control Protocol)
	- Industry standard protocol (IEEE 802.3ad)
	- Dynamic Negotiates the creation/maintenance of the EtherChannel.

- Static EtherChannel
	- A protocol isn't used to determine if an EtherChannel should be formed
	- Interfaces are statically configured to form an EtherChannel

`Note: Up to 8 interfaces can be fromed into a single EtherChannel (LACP allows up to 16, but only 8 will be active, the other 8 will be in standby mode, waiting for an active interface to fail`


## Configuration



- PAgP
![](images/Pasted%20image%2020231028160644.png)
![](images/Pasted%20image%2020231028160732.png)


- LACP
![](images/Pasted%20image%2020231028160812.png)

- Static Ether Channel Configuration

![](images/Pasted%20image%2020231028160941.png)


# Note

- Member interfaces must have matching configurations.
	- same duplex (full/half)
	- same speed
	- same switchport mode (access/trunk)
	- same allowed vlans/native vlan (for trunk interfaces)

- If an interface's configurations do not match the others, it will be excluded from the EtherChannel 


## show etherchannel summary

``
`show etherchannel summary`
![](images/Pasted%20image%2020231028162248.png)




# Layer 3 EtherChannel



![](images/Pasted%20image%2020231028162843.png)

![](images/Pasted%20image%2020231028162857.png)

![](images/Pasted%20image%2020231028162906.png)


----
----



# Commands


![](images/Pasted%20image%2020231028163031.png)