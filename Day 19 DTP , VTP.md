

## DTP (Dynamic Trunking Protocol)

- It is a cisco proprietary protocol which allows cisco switches to dynamically determine their interface status `access` or `trunk` without manual configuration
- DTP is enabled by default in cisco devices
- For security reasons, manual configuration is recommended over DTP.

![](images/Pasted%20image%2020231024170316.png)

## VTP (VLAN Trunking Protocol)

- VPT allows you to configure VLANs on a central VTP server switch, and other switches (VPT clients) will synchronize their VLAN database to the server
- It is designed for large network with many VLANs, so that you don't have to configure each VLAN on every switch
- It is rarely used, and recommended not to use at all.
- There are three VTP versions: 1,2,3
- There are three VTP modes: `server`, `client`, and `transparent`
- Cisco switches operate in VTP `server` mode by default