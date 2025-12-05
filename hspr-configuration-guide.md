# Cisco Packet Tracer - HSPR Configuration Guide
In this Packet Tracer Excersise I configure Hot Standyby Router Protocol (HSRP), which is Cisco Proprietary First Hop Redundancy Protocol (FHRP).

## Network Topology 



## Addressing Table 



## Verifying Connectivity 


## Configuring HSRP Active Router 

<img width="1400" height="1412" alt="image" src="https://github.com/user-attachments/assets/83bd9068-79ee-43bb-8b61-f5d2da14a234" />

## Configurig HSRP Standby Router 

<img width="1294" height="522" alt="image" src="https://github.com/user-attachments/assets/ebe100af-7cc9-4c73-b205-aea87ae91a18" />


## Verifying HSRP Operation 

R1 `show standby`
<img width="1266" height="394" alt="image" src="https://github.com/user-attachments/assets/e1c8d43d-16e4-46f8-bc5a-711ac6e405f5" />

R1 `show standby brief`
<img width="1274" height="160" alt="image" src="https://github.com/user-attachments/assets/139b61fc-0670-45a3-acab-ed812130df59" />


R3 `show standby`
<img width="1292" height="458" alt="image" src="https://github.com/user-attachments/assets/1ca7b763-14e6-43df-902f-5dee5c0e963a" />

R3 `show standby brief`

<img width="1268" height="160" alt="image" src="https://github.com/user-attachments/assets/fc8e5f4b-1aae-494e-a40f-d1596c3d3310" />

After configuring HSRP I also had to reconfigure default gateways for S1, S2, PC-A and PC-B. 

S1 reconfiguration using command `ip default gateway`
<img width="1396" height="1408" alt="image" src="https://github.com/user-attachments/assets/95f53ec7-4a90-4af1-bcf2-f6d41f9f3e01" />

<img width="1298" height="454" alt="image" src="https://github.com/user-attachments/assets/6b5dfbde-a584-4765-9015-ac686cf37339" />

After configuring I did the same for S2 and modified IP settings for both both end devices. 

<img width="1392" height="1410" alt="image" src="https://github.com/user-attachments/assets/aab65ada-39f5-448f-a282-ef345d10afdd" />

