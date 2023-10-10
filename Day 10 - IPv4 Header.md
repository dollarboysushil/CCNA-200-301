
![](images/Pasted%20image%2020231005135147.png)

---
---

# Version Field
- ### Length : 4 bits
- ### Identifies the version of IP used
	- #### IPv4 = 4 (0100 in binary)
	- #### IPv6 = 6 (0110 in binary)

# IHL - Internet Header Length
- ### Length : 4bits
- ### The final field of the IPv4 header (options) is variable in length , so this field is necessary to indicate the total length of the header
- ### Identifies the length of the header in 4byte increments
	- #### For example : Value of 5 = 5*4 bytes = 20 bytes 
- ### Minimum value is 5 (20 bytes)
- ### Maximum value is 15 (60 bytes)

# DSCP - Differentiated Services Code Point
- ### Length : 6 bits
- ### Used for QoS (Quality of Service)
- ### Used to prioritize delay-sensitive data

# ECN - Explicit Congestion Notification
- ### Length : 2 bits
- ### Provides end to end notification of network congestion __without dropping packets__.
- ### Optional feature that requires both endpoints, as well as the underlying network infrastructure, to support it.


# Total Length Field
- ### Length : 16bits
- ### Indicates the total length of the packet (L3 header + L4 segment)
- ### Measured in bytes (not 4-byte increments like IHL)
- ### Minimum value is 20 ( = IPv4 header with no encapsulated data)
- ### Maximum Value is 65,535

----
----

# Identification Field
- ### Length: 16bits
- ### If a packet id fragmented due to being too large, this field is used to identify which packet the fragment belongs to so that it can be re assembled again to make it original
- ### All fragments of the same packet will have their own IPv4 header with the same value in this field so they can be reassembled later
- ### Packets are fragmented if larger than MTU (Maximum Transmission Unit)
- ### MTU is usually 1500 bytes
- ### Fragments are reassembled by the receiving hosts



# Flags
- ### Length: 3bits
- ### Used to control/identifies fragments.
- ### Bit 0: Reserved , always set to 0
- ### Bit 1: Don't Fragment (DF bit), used to indicate a packet that should not be fragmented
- ### Bit 2: More Fragments (MF bit)
	- #### Set to 1 if there are more fragments in the packet
	- #### Set to 0 for the last fragment
	- #### Unfragmented packets will always have their MF bit set to 0



# Fragment Offset
- ### Length: 13 bits
- ### Used to indicate the position of the fragment within the original, unfragmented IP packet.
- ### Allows fragmented packets to be reassembled even if the fragments arrive out of order.


----
----


# Time To Live
- ### Length: 8 bits
- ### A router will drop a packet with a TTL of 0 
- ### Used to prevent infinite loops
- ### Originally designed to indicate the packets maximum lifetime in seconds
- ### In practice, indicates a 'hop count': each time the packet arrives at a router, the router decreases the TTL by 1
- ### Recommended default TTL of IPv4 Packet = 64


# Protocol
- ### Length: 8 bits
- ### Indicates the protocol of the encapsulated L4PDU
	- #### Value of 6: TCP
	- #### Value of 17: UDP
	- #### Value of 1: ICMP
	- #### Value of 89: OSPF (dynamic routing protocol)



# Header Checksum field
- ### Length: 16 bits
- ### A calculates checksum used to check for errors in IPv4 header.
- ### When a router receives a packet, it calculates the checksum of the header and compares it to the one in this field of the header
- ### If they do not match, the router drops the packet
- ### Used to check for errors only in the IPv4 header not in encapsulated data.
- ### Ip relies on the encapsulated protocol to detect errors in the encapsulated data.
- ### Both TCP and UDP have their own checksum fields to detect errors in the encapsulated data.


----
----

# Source/Destination IP Address 
- ### Length = 32 bits (each)
- ### Source IP Address = IPv4 Address of the sender of the packet
- ### Destination IP Address = IPv4 Address of the receiver of the packet

----
---

# Options Field
- ### It is optional and can be of length: 0-320 bits
- ### Rarely used
- ### If IHL > 5 ; Options are present

----
---

