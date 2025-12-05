# Cisco Packet Tracer - HSPR Configuration Guide
In this Packet Tracer Excersise I configure Hot Standyby Router Protocol (HSRP), which is Cisco Proprietary First Hop Redundancy Protocol (FHRP). 

HSRP basic idea is to create redundancy for end devices default gateway. By default devices can only have one default gateway address and if the configured router goes down hosts don't know how to use seconF router if there is no FHRP protocol configured. 

HSRP uses virtual router IP and MAC address to create one logical default gateway between multiple routers. One is active and another is standby router. If the active router goes down standby router takes over the role. 

## Network Topology 

<img width="1236" height="736" alt="image" src="https://github.com/user-attachments/assets/0141181c-1f49-4221-819f-2d4a2a65f1b9" />


## Addressing Table 

<img width="1248" height="892" alt="image" src="https://github.com/user-attachments/assets/e5899982-0965-4ccc-a6b6-52c59caead1e" />


## Verifying Connectivity 

I tested `tracert` -command from both hosts to the Web Server

PC-A
<img width="1398" height="742" alt="image" src="https://github.com/user-attachments/assets/59b2146f-8641-48fc-a3a7-dd37f487aedf" />

PC-B, as we can see from the tracert HSRP is not configured, because PC-B tracert could not find a path to the Web Server after I disconnected link between S3 and R3. 

<img width="1402" height="1638" alt="image" src="https://github.com/user-attachments/assets/f07749c9-0b4d-465e-a461-dabe01605cb8" />


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

After configuring HSRP I also had to reconfigure default gateways for S1, S3, PC-A and PC-B. 

S1 reconfiguration using command `ip default gateway`
<img width="1396" height="1408" alt="image" src="https://github.com/user-attachments/assets/95f53ec7-4a90-4af1-bcf2-f6d41f9f3e01" />

<img width="1298" height="454" alt="image" src="https://github.com/user-attachments/assets/6b5dfbde-a584-4765-9015-ac686cf37339" />

After configuring I did the same for S2 and modified IP settings for both both end devices. 

<img width="1392" height="1410" alt="image" src="https://github.com/user-attachments/assets/aab65ada-39f5-448f-a282-ef345d10afdd" />

Now I have configured simple HSRP setup. 
