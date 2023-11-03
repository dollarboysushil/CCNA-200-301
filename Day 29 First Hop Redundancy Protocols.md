

## Topics we will cover

- [The Purpose of FHRPS (First Hop Redundancy)](#fhrps)
- [HSRP (Hot Standby Router Protocol)](#hsrp)
- VRRP (Virtual Router Redundancy Protocol)
- GLBP (Gateway Load Balancing Protocol)
- Basic HSRP Configuration


## FHRP Intro <a id="fhrps"></a>

![](images/Pasted%20image%2020231103095735.png)
In above network, R1s IP 172.16.0.254 is set as `default gateway` which means each pc is configured with the 172.16.0.254 address as its default gateway

![](images/Pasted%20image%2020231103095513.png)
 R1 goes down due to hardware failure. Fortunately we have our backup router R2 . But there is a problem.  
 Problem = PCs default gateway is still set to 172.16.0.254 (R1s address). Although backup router is available, Pcs don't know that R1 is down . Here PC tries to send traffic to R1

`Here comes FHRP (First Hop Redundancy Protocol) in help. Which causes R2 to automatically become the new default gateway if R1 is no longer available`

![](images/Pasted%20image%2020231103100354.png)


## Here is how FHRP do this

![](images/Pasted%20image%2020231103101351.png)![](images/Pasted%20image%2020231103101441.png)



## HSRP (Hot Standby Router Protocol) <a id="hsrp"></a>

![](images/Pasted%20image%2020231103102154.png)

## VRRP (Virtual Router Redundancy Protocol)

![](images/Pasted%20image%2020231103102930.png)

## GLBP (Gateway Load Balancing Protocol)

![](images/Pasted%20image%2020231103103313.png)


## HSRP / VRRP / GLBP

![](images/Pasted%20image%2020231103103345.png)



## Configuration for HSRP

![](images/Pasted%20image%2020231103103607.png)
![](images/Pasted%20image%2020231103103818.png)
![](images/Pasted%20image%2020231103103856.png)![](images/Pasted%20image%2020231103104008.png)

