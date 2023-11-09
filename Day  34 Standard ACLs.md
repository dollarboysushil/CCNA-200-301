
## What we will cover.
- What are ACLs?
- ACL login
- ACL types
- Standard numbered ACLs
- Standard named ACLs


## What are ACLs?
![](images/Pasted%20image%2020231109092923.png)


## How ACLs work?
![](images/Pasted%20image%2020231109093327.png)
![](images/Pasted%20image%2020231109093852.png)
![](images/Pasted%20image%2020231109094124.png)


## Implicit deny

![](images/Pasted%20image%2020231109094302.png)


## ACL Types

![](images/Pasted%20image%2020231109094447.png)
`Day 35 = Extended ACLs`

## Standard Numbered ACLs

![](images/Pasted%20image%2020231109100601.png)
`here 1st three commands are used to deny the host 1.1.1.1. Three ways are shown.`
`next two commands are used to permit all other traffic (traffic are blocked due to implicit deny`
`Last command is used as description`

![](images/Pasted%20image%2020231109104656.png)


## Examples

![](images/Pasted%20image%2020231109105129.png)



---
Commands summary

|SN| **Layers**      | Description |
|---| ----------- | ----------- |
|1 |access-list number {deny / permit} ip wildcard-mask| configure standard numbered acl|
|2|access-list number remark ##remarks ##|set description for acl|
|3| do show access-lists | list all the access lists|
|4| do show ip access-lists | only list ip access-lists|

----


## Standard Named ACLs

![](images/Pasted%20image%2020231109105925.png)
![](images/Pasted%20image%2020231109105955.png)


Example.
![](images/Pasted%20image%2020231109110257.png)
