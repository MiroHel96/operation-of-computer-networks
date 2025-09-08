# Cisco Packet Tracer - Configure Router-on-a-Stick Inter-VLAN Routing

In this excersise I confiure Cisco router to work in Router-on-a-Stick Inter-Vlan routing. 

Topology of the network. 

<img width="640" height="323" alt="image" src="https://github.com/user-attachments/assets/f644fccb-389c-480f-bbd3-517f0f31bf3d" />


Addressing Table for the Network: 

<img width="768" height="191" alt="image" src="https://github.com/user-attachments/assets/aed903c9-6707-4670-a142-57edfb1c546c" />


## Adding Vlans to switch

First I had to create VLAN10 and VLAN30 for Switch1. I openend CLI and entered to EXCEC mode and from there to configuration mode. 
I issued commands "vlan 10" and "vlan 30" to create both VLANs. After that I veriefied that they were created.

<img width="634" height="454" alt="image" src="https://github.com/user-attachments/assets/78c1ada9-0ee0-48f7-96ec-367b1c5fabf0" />

After configuration I had to do ping test from PC1 to PC3. As excepted the ping failed because both host are on a different network. 

<img width="701" height="715" alt="image" src="https://github.com/user-attachments/assets/888c4de3-ecba-4ef3-867a-5a3670bb6b8b" />

After this I added correct VLAN for each interace. 

<img width="635" height="325" alt="image" src="https://github.com/user-attachments/assets/5c66f72a-652e-485e-b842-575257077cdb" />

<img width="636" height="355" alt="image" src="https://github.com/user-attachments/assets/acbda76d-6976-4f1a-850d-afc3e10483b6" />


## Configure Subinterfaces 

Next I had to configure Subinterfaces for VLAN10 and 30. Subinterface is one interface which is split into logical separate interfaces.  

For the interface G0/0.10 I used the following commands:
 - R1(config)# int g0/0.10
 - R1(config-subif)# encapsulation dot1Q 10R1
 - (config-subif)# ip address 172.17.10.1 255.255.255.0

<img width="637" height="249" alt="image" src="https://github.com/user-attachments/assets/37a1821b-e145-4ed6-87c3-b7fdec90d703" />

After configuring G0/0.10 interface I veried that it was configured correctly.

<img width="630" height="115" alt="image" src="https://github.com/user-attachments/assets/3c3d951f-ecbe-421a-a8c6-4f0234056d42" />

Next I did the same configurations for interface G0/0.30, but with different IP addressing and subnetmask.

<img width="638" height="118" alt="image" src="https://github.com/user-attachments/assets/6c087d99-0baf-4209-b255-8ebb842334f7" />

After configurating both subinterfaces I turned on G0/0 interface. 

<img width="632" height="273" alt="image" src="https://github.com/user-attachments/assets/d9b68256-cd95-4c38-8421-bb4752f5a96e" />

## Test Connectivity with Inter-VLAN Routing 

Now both VLAN interfaces are configured to the router and It should know where to send the packet, but it does not work yet and why is that? 
Router in the network does not have interface configured to trunk. It has to be configured because it was configured with multiple interaces. 

<img width="696" height="711" alt="image" src="https://github.com/user-attachments/assets/56507f29-b4f1-4cc0-88b8-e9aff6dcd917" />

<img width="641" height="251" alt="image" src="https://github.com/user-attachments/assets/20068c60-31ac-43c3-b3a7-fc8c9048bd3b" />

<img width="637" height="210" alt="image" src="https://github.com/user-attachments/assets/1176d936-08af-4ced-9669-33552c98c45e" />

After configuring trunking to G0/1 I tested the ping and it worked as excepted. 






