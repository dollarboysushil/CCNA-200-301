
## Topics we will cover
- Hexadecimal (review)
- Why IPv6
- Basics of IPv6
- Configuring IPv6 addresses

## Hexadecimal

![](images/Pasted%20image%2020231105123759.png)
![](images/Pasted%20image%2020231105123815.png)
![](images/Pasted%20image%2020231105123842.png)
![](images/Pasted%20image%2020231105123902.png)


## Why  IPv6?
![](images/Pasted%20image%2020231105124535.png)

![](images/Pasted%20image%2020231105124712.png)


## IPv6 Intro
![](images/Pasted%20image%2020231105125056.png)

## Shortening IPv6 addresses
![](images/Pasted%20image%2020231105125230.png)

![](images/Pasted%20image%2020231105125328.png)

#### Examples
![](images/Pasted%20image%2020231105125545.png)


## Expanding IPv5
![](images/Pasted%20image%2020231105125704.png)

#### Examples
![](images/Pasted%20image%2020231105125946.png)


## Finding the IPv6 Prefix (global unicast addresses)
`change all of the host bit to zero = network address`

![](images/Pasted%20image%2020231105144200.png)

#### Examples
![](images/Pasted%20image%2020231105144407.png)
![](images/Pasted%20image%2020231105144518.png)
`if prefix length is not multiple of 4 then `

![](images/Pasted%20image%2020231105144912.png)

#### Examples
![](images/Pasted%20image%2020231105144953.png)


## Configuration

![](images/Pasted%20image%2020231105145145.png)
`lets confirm the configuration`

![](images/Pasted%20image%2020231105145649.png)

---
----
----


|SN| **Commands**      | Description |
|---| ----------- | ----------- |
|1| ipv6 unicast-routing      |Allows router to perform IPv6 routing.    |
|2| int g0/0| selecting the interface|
|3| ipv6 address {address}|configuring the  ipv6 address |
|4|show ipv6 interface brief ||

