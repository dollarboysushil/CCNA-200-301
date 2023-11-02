

## Topics we will cover
- OSPF network types
- OSPF neighbor/adjacency requirement
- OSPF LSA types



## Loopback Interfaces

![](images/Pasted%20image%2020231102171752.png)


## OSPF Network Types

![](images/Pasted%20image%2020231102171825.png)


----
----
----

## Broadcast Network Type

![](images/Pasted%20image%2020231102172131.png)


## Broadcast - DR/BDR Election

![](images/Pasted%20image%2020231102172302.png)

`show ip interface g0/0`

FOR R5
![](images/Pasted%20image%2020231102172501.png)

FOR R2
![](images/Pasted%20image%2020231102172624.png)


## Changing OSPF interface Priority

![](images/Pasted%20image%2020231102172806.png)
![](images/Pasted%20image%2020231102172814.png)
`here R2 state is still DROTHER even though it has higher priority
it is because:

![](images/Pasted%20image%2020231102172921.png)`

it is bad idea to reset OSPF 
here is how to reset OSPF


![](images/Pasted%20image%2020231102173452.png)
![](images/Pasted%20image%2020231102173422.png)

![](images/Pasted%20image%2020231102173643.png)



`If 5 routers are connected to the same segment and the all share LSAs with each other, it will end up like this. A whole lot of LSAs flooding and congesting the network.`
![](images/Pasted%20image%2020231102173901.png)

`How about if we use the DR and BDR?`
![](images/Pasted%20image%2020231102173928.png)
we can clearly see the number of LSAs flooding around the network is reduced.
![](images/Pasted%20image%2020231102174050.png)


![](images/Pasted%20image%2020231102174131.png)




![](images/Pasted%20image%2020231102174244.png)`F= number of full adjacencies = 2 = R2 and R4`
`c= total count of neighbors = 3 = R2 ,R4 and R5`

Here is the full detail
![](images/Pasted%20image%2020231102174508.png)


----
---
---


## Point To Point Network Type


![](images/Pasted%20image%2020231102174803.png)



![](images/Pasted%20image%2020231102174850.png)


![](images/Pasted%20image%2020231102175003.png)



![](images/Pasted%20image%2020231102175052.png)


![](images/Pasted%20image%2020231102175137.png)

![](images/Pasted%20image%2020231102175155.png)

## `how to know which side is dte and which side is dce`

![](images/Pasted%20image%2020231102175253.png)


### Summary for Serial Connection
![](images/Pasted%20image%2020231102180427.png)


## Point to Point Network Type continue
![](images/Pasted%20image%2020231102180544.png)

`reason for  - 
`because the point to point network type doesnot use DRs or BDRs`

---
----
----

## Manually configure OSPF network type

![](images/Pasted%20image%2020231102180745.png)

`why do we need to manually configure network type`

![](images/Pasted%20image%2020231102180819.png)


----
---
---
## Broadcast vs Point-to-Point Chart

![](images/Pasted%20image%2020231102180855.png)




----
---
---
---

## OSPF Neighbor Requirements


- Area number must match
	- ![](images/Pasted%20image%2020231102181843.png)
	- ![](images/Pasted%20image%2020231102181853.png)


- Interfaces must be in the same subnet
	- ![](images/Pasted%20image%2020231102181951.png)
	- ![](images/Pasted%20image%2020231102182008.png)


- OSPF process must not be shutdown
	- ![](images/Pasted%20image%2020231102182150.png)



- OSPF Router IDs must be unique
	- ![](images/Pasted%20image%2020231102182412.png)



- Hello and Dead timers must match
	- ![](images/Pasted%20image%2020231102182947.png)


- Authentication setting must match
	- ![](images/Pasted%20image%2020231102183121.png)


- IP MTU must match
	- IP MTU is the maximum size of an IP packet that will be sent out of the interface
	- The default is usually 1500 bytes and can be configured
	- ![](images/Pasted%20image%2020231102183907.png)


- OSPF Network Type Must Match
	- ![](images/Pasted%20image%2020231102184007.png)
	- ![](images/Pasted%20image%2020231102184033.png)
	- `R2s loopback address is not in R1 routing table`




#### Conclusions
![](images/Pasted%20image%2020231102184112.png)


---
----
----
----


## OSPF LSA Types

![](images/Pasted%20image%2020231102184317.png)

![](images/Pasted%20image%2020231102184410.png)

## ` lsdb on R1`
![](images/Pasted%20image%2020231102184534.png)


