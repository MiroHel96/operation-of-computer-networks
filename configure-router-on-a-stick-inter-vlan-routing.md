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


## Configure Subinterfaces 




## Test Connectivity with Inter-VLAN Routing 


