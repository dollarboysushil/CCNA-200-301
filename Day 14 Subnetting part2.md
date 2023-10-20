![](images/Pasted%20image%2020231010201755.png)


- ## For each burrowed bits , number of subnets doubles
- ## For each host bits , number of addresses in each subnets doubles

# Example


For prefix Length /17

burrowed bits = 1
number of subnets = 2^1 =2
number of hosts = remaining bits= 32-17 = 15; 2^15 -2 = 32766


----
---
Ip = 10.217.182.223/11


1) Network Address: 
		convert to binary
			***00001010.110***11001.10110110.11011111
		change all host bits to zero
			***00001010.110***00000.00000000.00000000
		change back to decimal
			10.192.0.0


2) Broadcast address
		change all host bits to one
			***00001010.110***11111.11111111.11111111
		change back to decimal
			10.223.255.255


3) First usable address
		Network address + 1
			10.192.0.1


4) Last usable address
		Broadcast address -1
			10.223.255.254


5) Number of host (usable) addresses:
		2^no of host bits -2
			2^21-2 = 2097150


6) Number of valid subnets
		There are 2^x subnets in a network, where x is the number of borrowed subnet bits.


6) Subnet mask 
		convert all the network portion to 1 and host to 0


![](images/Pasted%20image%2020231011092440.png)