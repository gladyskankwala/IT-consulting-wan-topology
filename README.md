# Medium-IT-Enterprise-network-topology
Medium WAN enterprise network topology project
1.Network topology 
the network is design to prevent failures by using at least two connections with other branches, the central hub is HQ Windhoek which is connected to all individual branches

2.IP addressing using VLSM
I use the IP 172.27.0.0/19 which was divide into small subnet in order to meet requirement respecting the expected grow of the company from 505 workers to 2020 workers by 2030 of the IT consulting firm
-the company will have 4 time the number of current workers by 2030

each branch's current workers number will be multiple by 4 to meet the expectation and divide by 3 for each individual VLANs
WINDHOEK--
255*4 = 1020 => 1020/3 = 340 workers per VLAN
340 = /23: 510 usable IP address 
VLAN 1: IT = 172.27.0.0/23
VLAN 2: HR = 172.27.2.0/23
VLAN 3: FINANCE = 172.27.4.0/23

OSHAKATI--
90*4 = 360 => 360/3 = 120 workers per VLAN
120 = /25
VLAN 1: IT(by default): 172.27.6.0/25
VLAN 2: HR(by default): 172.27.6.128/25
VLAN 3: FINANCE(by default): 172.27.7.0/25

LUDERITZ---
72*4 = 288 => 288/3 = 96 workers per VLAN
96 = /25
VLAN 1: IT(by default): 172.27.128/25
VLAN 2: HR(by default): 172.27.8.0/25
VLAN 3: FINANCE(by default): 172.27.8.128/25

MARIENTAL--
33*4 = 132 => 132/3 = 44 workers per VLAN
44 = /26
VLAN 1: IT(by default): 172.27.9.0/26
VLAN 2: HR(by default): 172.27.9.64/26
VLAN 3: FINANCE(by default): 172.27.9.128/26

OPUWO--
29*4 = 116 => 116/3 = 38.67 = 39 workers per VLAN
39 = /26
VLAN 1: IT(by default): 172.27.9.192/26
VLAN 2: HR(by default): 172.27.10.0/26
VLAN 3: FINANCE(by default): 172.27.10.64/26

GROOTFONTEIN--
27*4 = 108 => 108/3 = 36 workers per VLAN
36 = /26
VLAN 3: FINANCE(by default): 172.27.10.128/26
VLAN 3: FINANCE(by default): 172.27.10.192/26
VLAN 3: FINANCE(by default): 172.27.11.64/26

Notice: this subnet are calculate according the current number of users and the future expansion

Links IP addressing
WINDHOEK Links IP configuration---
to OSHAKATI : 172.27.11.68/30
to GROOTFONTEIN : 172.27.11.72/30
to MARIENTAL : 172.27.11.76/30
to OPUWO : 172.27.11.80/30
to LUDERITZ : 172.27.11.84/30

OSHAKATI link to MARIENTAL
172.27.11.88/30

MARIENTAL link to OPUWO
172.27.11.92/30

OPUWO link to LUDERITZ
172.27.11.96/30

LLUDERITZ link to GROOTFONFEIN
172.27.11.100/30

3.Routing Protocol

OSPF is one of the most use routing protocol in large network, used under one area (area 0)

WINDHOEK network configuration---
172.27.0.0 0.0.1.255 area 0
172.27.2.0 0.0.1.255 area 0
172.27.4.0 0.0.1.255 area 0
172.27.11.68 0.0.0.3 area 0
172.27.11.72 0.0.0.3 area 0
172.27.11.76 0.0.0.3 area 0
172.27.11.80 0.0.0.3 area 0
172.27.11.84 0.0.0.3 area 0

OSHAKATI network configuration---
172.27.6.0 0.0.0.127 area 0
172.27.6.128 0.0.0.127 area 0
172.27.7.0 0.0.0.127 area 0
172.27.11.68 0.0.0.3 area 0
172.27.11.88 0.0.0.3 area 0

MARIENTAL network configuration---
172.27.9.0 0.0.0.63 area 0
172.27.9.64 0.0.0.63 area 0
172.27.9.128 0.0.0.63 area 0
172.27.11.76 0.0.0.3 area 0
172.27.11.88 0.0.0.3 area 0
172.27.11.92 0.0.0.3 area 0

OPUWO network configuration---
172.27.9.192 0.0.0.63 area 0
172.27.10.0 0.0.0.63 area 0
172.27.10.64 0.0.0.63 area 0
172.27.11.92 0.0.0.3 area 0
172.27.11.96 0.0.0.3 area 0
172.27.11.80 0.0.0.3 area 0

LUDERITZ network configuration---
172.27.7.128 0.0.0.127 area 0
172.27.8.0 0.0.0.127 area 0
172.27.8.128 0.0.0.127 area 0
172.27.11.96 0.0.0.3 area 0
172.27.11.100 0.0.0.3 area 0
172.27.11.84 0.0.0.3 area 0

GROOTFONTEIN
172.27.10.128 0.0.0.63 area 0
172.27.10.192 0.0.0.63 area 0
172.27.11.0 0.0.0.63 area 0
172.27.11.100 0.0.0.3 area 0
172.27.11.72 0.0.0.3 area 0
