# OSPF-SINGLE-AREA
OSPF SINGLE AREA 
----------------

R1
---

R1(config)#int g0/0
R1(config-if)#ip address 12.0.0.1 255.255.255.0
R1(config-if)#no shutdown 
R1(config)#exit

R1(config)#int g0/1
R1(config-if)#ip address 10.0.0.1 255.0.0.0
R1(config-if)#no shutdown 
R1(config-if)#exit

R2
---

R2(config)#int g0/0
R2(config-if)#ip address 12.0.0.2 255.255.255.0
R2(config-if)#no shutdown 
R1(config-if)#exit

R2(config)#int g0/1
R2(config-if)#ip address 13.0.0.1 255.255.255.0
R2(config-if)#no shutdown 
R1(config-if)#exit

R2(config)#int g0/2
R2(config-if)#ip address 20.0.0.1 255.0.0.0
R2(config-if)#no shutdown 
R1(config-if)#exit

R3
----

R3(config)#int g0/0
R3(config-if)#ip address 13.0.0.2 255.255.255.0
R3(config-if)#no shutdown 
R1(config-if)#exit

R3(config)#int g0/1
R3(config-if)#ip address 30.0.0.1 255.0.0.0
R3(config-if)#no shutdown 


router mode ospf
---------------

R1
-----
R1(config)#router ospf 1
R1(config-router)#router-id 1.1.1.1
R1(config-router)#network 10.0.0.0 0.255.255.255 area 1
R1(config-router)#network 12.0.0.0 0.0.0.255 area 1

R2
----
R2(config)#router ospf 1
R2(config-router)#router-id 2.2.2.2
R2(config-router)#network 12.0.0.0 0.0.0.255 area 1
R2(config-router)#network 13.0.0.0 0.0.0.255 area 1
R2(config-router)#network 20.0.0.0 0.255.255.255 area 1

R3
----
3(config)#router ospf 1
R3(config-router)#router-id 3.3.3.3
R3(config-router)#network 13.0.0.0 0.0.0.255 area 1
R3(config-router)#network 30.0.0.0 0.255.2525
R3(config-router)#network 30.0.0.0 0.255.255.255 area 1

Passive interface
-----------------
R1(config)#passive-interface g0/1
R2(config)#passive-interface g0/1
R3(config)#passive-interface g0/1
![OSPF SINGLE AREA LAB](https://user-images.githubusercontent.com/106605770/177992667-fab410af-b734-4e46-884a-2371c3062c7b.jpg)
