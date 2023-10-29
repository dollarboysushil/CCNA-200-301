

## Topics we'll cover

- Intro to dynamic routing protocols
- Types of dynamic routing protocols
- Dynamic routing protocol metrics
- Administrative distance


### Network Route: A route  to a network/subnet (mask length < /32)
### Host Route: A route to a specific host (/32 mask)
![](images/Pasted%20image%2020231029152449.png)![](images/Pasted%20image%2020231029152459.png)
![](images/Pasted%20image%2020231029152517.png)


## Dynamic Routing

- Routers can use dynamic routing protocols to advertise information about the routes they know to other routers.
- They form `adjacencies`/ `neighbor relationship` / `neighborships` with adjacent routers to exchange this info.
	- ![](images/Pasted%20image%2020231029160450.png)
	- For eg. `R1` will form `adjancies` with `R2` and `R3` 
- If multiple routes to the destination are learned, the router determines which route is superior and adds it to the routing table. It uses `metric` of the route to decide which is superior (`lowest metric = superior`).



## Different Types of Routing Protocol

- IGP (Interior Gateway Protocol)
	- used to share routes within a single `autonomous system (AS)`, which is a single organization (company)
- EGP (Exterior Gateway Protocol)
	- used to share routes between different autonomous system

![](images/Pasted%20image%2020231029161650.png)

----
---

![](images/Pasted%20image%2020231029161754.png)

`Algorithm is process each protocol uses to share routes information and choose the best route to each destination.`



## Distance Vector Routing Protocols

- Distance Vector protocols were invented before link state protocols.
- Early example are `RIPv1` and cisco's proprietary protocol `IGRP` (which was updated to `EIGRP`)
- Distance vector protocols operate by sending the following to their directly connected neighbors:
	- their known distance networks
	- their metric to reach their known destination networks
- This method of sharing route information is often called '`routing by rumor`'
- This is because the router does not know about the network beyond its neighbors. It only knows the information that its neighbors tell it.
- It is called `Distance vector` because the routers only learn the `distance (metric)` and `vector (direction, the next hop router)` of each route.

![](images/Pasted%20image%2020231029165514.png)


## Link State Routing Protocols

- When using a link state routing protocols, every router creates a `connectivity map` of the network.
- To allow this, each router advertises information about its `interfaces` (connected networks) to its neighbor. This advertisements are passed along to other routers, until all routers in the network develop the same map of the network.
- Each router independently uses this map to calculate the best routes to each destination.
- Link state protocols use more resources (CPU) on the router, because more information is shared.
- However, link state protocols tend to be faster in reacting to changes in the network than distance vector protocols.


## Metrics

- A routers route table contains the best route to each destination network it knows about.
- If a router using a dynamic routing protocol learns two different routes to the same destination, how does it determine which is best?
- It uses the metric value of the routes to determine which is best. lower = best
- Each routing protocol uses a different metric to determine which route is the best.

![](images/Pasted%20image%2020231029172933.png)

- Here in this network diagram Router R1 learns two path to 192.168.4.0/24 (one via r2 and one via r3) , only the route via R2 is added to the routing table. Because the Fast Ethernet connection has higher metric cost than the other gigabit ethernet connection. 


#### What if both were gigabit ethernet connection? Both route would have same cost, which route would be added to the route table?

![](images/Pasted%20image%2020231029173402.png)
![](images/Pasted%20image%2020231029173412.png)


![](images/Pasted%20image%2020231029173954.png)

`ECMP`= Second value in the square bracket (red one) is the metric value of the route.
			Both routes have metric of 3, so both were added and traffic will be load balanced over both routes. This is called `ECMP= Equal Cost Multi-Path`
`AD (administrative distance)` = Highlighted with blue. More about it later.



---
---

## IGP Metric Charts


![](images/Pasted%20image%2020231029174251.png)
`overall aim : let the router select the best route to the destination, only difference is some might make better decisions than others.`
#### Example

![](images/Pasted%20image%2020231029174434.png)


----
-----
## AD (Administrative Distance)


`Lower AD is preferred`
![](images/Pasted%20image%2020231029174728.png)

![](images/Pasted%20image%2020231029174758.png)


#### QUIZ

![](images/Pasted%20image%2020231029175202.png)


-----
-----
## Configure AD to static route

![](images/Pasted%20image%2020231029175810.png)![](images/Pasted%20image%2020231029175848.png)

![](images/Pasted%20image%2020231029175924.png)

