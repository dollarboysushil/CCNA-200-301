
---
___
---
# OSI MODEL (Open system interconnection)


|SN| **Layers**      | Description |
|---| ----------- | ----------- |
|7| Application      | HTTP /HTTPS  , SMTP , FTP etc      |
|6| Presentation   |   translate between data formats|
|5| Session   |        |
|4| Transport   |         |
|3| Network   |  Routers operate here       |
|2| Data Link   |    Switches     |
|1| Physical   |         |


- ## Layer 7,6 & 5 are The Upper Layers 
- ## Network Engineers dont usually work with The Upper Layers
- ## Application developers works on the upper layers to connect their application over networks
---
---
---


# 7) Application

- Closest to end user
- Interacts with software application (eg; Brave , Firefox , Chrome ..)
- HTTP and HTTPS are layer7 protocols

__*Functions*__
- Identifying communication partners
- synchronizing communication


![500*500](images/Pasted%20image%2020230916191313.png)
![500*500](images/Pasted%20image%2020230916191947.png)
![500*500](images/Pasted%20image%2020230916192013.png)
![500*500](images/Pasted%20image%2020230916192031.png)


- The software application (may be a web browser) interacts with layer 7 and wants to send some data to the system on the right .
- This data is processed through the OSI stack , adding something to the original , this is called <u><b><font color='red'>ENCAPSULATION</font></b></u> as the original data is encapsulated inside this additional information which is added on . 
- Receiving System does the opposite process i.e addition are stripped off until the data reaches the Layer 7 (This process is called <u><b><font color='red'>De-ENCAPSULATION </font></b></u> )
- Both <u><b><font color='red'>ENCAPSULATION </font></b></u>and <u><b><font color='red'>De-ENCAPSULATION </font></b></u> Process are examples of <u><b><font color='yellow'>"Adjacent-Layer interaction" </font></b></u> _But_ communication between the application layers of the two different system is called <u><b><font color='yellow'>"Same-layer interaction" </font></b></u>
- <u><b><font color='yellow'>"Same-layer interaction" </font></b></u> between layer 7 allows its functions as above mentioned


# 6) Presentation
 
 _Functions_
 - Translate between application and network formats
- Encryption of data as it is send and decryption of data as it is received

![500](images/Pasted%20image%2020230916192431.png)


# 5) Session Layer

![500](images/Pasted%20image%2020230916192549.png)


# 4) Transport Layer

![500](images/Pasted%20image%2020230916193149.png)


![500](images/Pasted%20image%2020230916193750.png)
- Data is prepared by top 3 layers
- Layer 4 header is added on. Here this unit of DATA plus Layer 4 header is called a Segment
- If data being sent is large , then it is segmented into smaller parts and Layer 4 header will be added on to each segment

### Then this segment is passed on to layer 3 (Network Layer)


# 3) Network Layer

![500](images/Pasted%20image%2020230916194057.png)

![500](images/Pasted%20image%2020230917082536.png)
- Network layer adds the Layer 3 Header (info like source and destination ip address comes under layer 3 header) 
- Combination of Data + Layer4 header+ Layer 3 header is called Packet



# 2) Data Link Layer

![500](images/Pasted%20image%2020230917082653.png)

![500](images/Pasted%20image%2020230917082808.png)


# 1) Physical Layer


![500](images/Pasted%20image%2020230917082940.png)


# * Protocol Data Units (PDUs) *

![500](images/Pasted%20image%2020230917083236.png)



----
----
---


# TCP / IP Suite

![500](images/Pasted%20image%2020230917083434.png)

![500](images/Pasted%20image%2020230917083549.png)



![](images/Pasted%20image%2020230917093450.png)