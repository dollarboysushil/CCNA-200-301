

## Topics we will cover

1. IPv6 address Configuration (continue)
	- Modified EUI-64
2. IPv6 address types
	- Global unicast
	- Unique local
	- Link local
	- Multicast
	- Others...


## Configuring IPv6 Address
![](images/Pasted%20image%2020231106094912.png)
`This is the interface id which is 64 bits. It will be added to network prefix to make a complete ipv6 address.`

Here are some practice questions.
![](images/Pasted%20image%2020231106095345.png)

## EUI-64 Configuration
![](images/Pasted%20image%2020231106100832.png)
![](images/Pasted%20image%2020231106100621.png)

|SN| **Commands**      | Description |
|---| ----------- | ----------- |
|1|int g0/0|select interface|
|2| ipv6 address `2001:db8::/64` eui-64|` `is network prefix|
|3|no shutdown||

## EUI-64 Summary

`EUI-64 allows routers to automatically generate IPv6 address by expanding their MAC address to 64 interface ID which is then combined with specified IPv6 address prefix`.
EUI-64  is not really a type of IPv6 address, it is a method of automatically generating an IPv6 address using a specified prefix and a Mac address.


-----
----
---
# IPv6 Address Types

## 1. Global Unicast

![](images/Pasted%20image%2020231106102207.png)
`first 64bits are network prefix and last 64 bits are host portions`

## 2. Unique Local

![](images/Pasted%20image%2020231106102606.png)


## 3. Link Local

![](images/Pasted%20image%2020231106103124.png)


## 4. Multicast

![](images/Pasted%20image%2020231106103449.png)
![](images/Pasted%20image%2020231106103533.png)

#### Multicast address scopes

![](images/Pasted%20image%2020231106103908.png)
`lets look at a diagram to visualise the scopes`

![](images/Pasted%20image%2020231106104106.png)
` aside from interface-local and link-local the actual boundaries of each scope needs to be defined by the network engineer.`


## 5. Anycast

![](images/Pasted%20image%2020231106104641.png)
![](images/Pasted%20image%2020231106104829.png)


# Other IPv6 Addresses

![](images/Pasted%20image%2020231106105222.png)
