

## What we will cover.
- Another way to configure numbered ACLs
- Editing ACLs
- Extended numbered and named ACLs


## Configuring numbered ACLs with subcommands

![](images/Pasted%20image%2020231110093413.png)

![](images/Pasted%20image%2020231110093515.png)

#### Advantages of named ACL config mode

1. ![](images/Pasted%20image%2020231110093648.png)
![](images/Pasted%20image%2020231110093715.png)
`When configuring/edition numbered ACLs from global config mode, you can't delete individual entries, you can only delte the entire ACL.`

2. ![](images/Pasted%20image%2020231110094000.png)


### Resequencing ACLs

![](images/Pasted%20image%2020231110094227.png)
`here in the beginning sequence number are 1,2,3,4,5 . It is impossible to add new entries in between. So we can use the resequencing function to change 1234 to 10,20,30,40,50 so that we can add new entry in between.`



---
---

## Extended ACLs

![](images/Pasted%20image%2020231110095152.png)

#### Matching the protocol

![](images/Pasted%20image%2020231110100158.png)
![](images/Pasted%20image%2020231110100107.png)
![](images/Pasted%20image%2020231110095920.png)
`Deny all packets that encapsulate a TCP segment, from any source, to destination 10.0.0.0/24`


#### Practice
![](images/Pasted%20image%2020231110100318.png)


more...............................................................................................................................................................
