# Cisco Packet Tracer -  Configure Layer 3 Switching and Inter-VLAN Routing

# Network Topology
<img width="693" height="412" alt="image" src="https://github.com/user-attachments/assets/966f2af3-d677-455c-93d7-06cdb49b2f7b" />

# Addressing Table 

<img width="760" height="599" alt="image" src="https://github.com/user-attachments/assets/d71af68b-4a6f-41e7-93e7-0a6c054d0f6d" />

# Part 1 Configure Layer 3 Switch 

First I opened MLS CLI and configured G0/2 as a routed port and assigned an IP address for it.

<img width="637" height="57" alt="image" src="https://github.com/user-attachments/assets/0a2ef172-c7ac-427c-9f6b-e94242e7796e" />

After configuration I tested connectivity to Cloud by pinging it. The ping was succesfull. 

<img width="630" height="108" alt="image" src="https://github.com/user-attachments/assets/137fe919-a72d-490f-86e8-ea2afd9f6407" />


# Part 2 Configure Inter-VLAN Routing

Next I configured VLANs for MLS.

I checked initial VLAN settings for MLS, before configuring them.

<img width="631" height="257" alt="image" src="https://github.com/user-attachments/assets/f0af678f-1c93-4f8e-ad15-f33c5f59663d" />

Next I configuredd VLANS:
- VLAN 10, Staff
- VLAN 20, Stundent
- VLAN 30, Faculty

<img width="635" height="299" alt="image" src="https://github.com/user-attachments/assets/0daaf073-9355-4e5d-a061-afba54e45e71" />

<img width="633" height="249" alt="image" src="https://github.com/user-attachments/assets/9974c1b1-3346-416c-98ca-e166585482d9" />

Next I configured SVI for MLS each VLAN. 

<img width="629" height="397" alt="image" src="https://github.com/user-attachments/assets/6d06dd16-1ce9-4c9e-8a9a-9fb47776fe0a" />

<img width="633" height="72" alt="image" src="https://github.com/user-attachments/assets/87765f75-44fb-442a-adc4-524d16cee542" />

After configurin IP addresses for each VLAN SVI interface, I configured G0/1 as a static trunk port for MLS. 

<img width="632" height="299" alt="image" src="https://github.com/user-attachments/assets/4027eac2-523c-4b20-a40b-6c77266d131a" />

<img width="631" height="160" alt="image" src="https://github.com/user-attachments/assets/627ebf0d-d38b-43f9-a4f2-a943e6546d52" />

<img width="634" height="298" alt="image" src="https://github.com/user-attachments/assets/d31fb7b5-f593-422f-8f1a-160363c2b92f" />

Next I had to configure S1 with trunking because there is a native VLAN mismatch. Both ends of interfaces has to be configured with trunking. 

<img width="633" height="519" alt="image" src="https://github.com/user-attachments/assets/bdb37aa8-6619-4d31-9259-ee8c507759de" />

After configuring trunking for MLS and S1 I enabled routing in MLS. 

<img width="638" height="457" alt="image" src="https://github.com/user-attachments/assets/82dff751-9a27-41f5-a09b-b37ab1fabd3a" />

Finally I verfied connectivity. Ping did not work wor any of the switches or between MLS. I did not have VLAN99 IP address configured. I configured IP address for VLAN 99 to both interfaces.

<img width="636" height="342" alt="image" src="https://github.com/user-attachments/assets/5d89f856-c6cf-48da-800d-0b63f1902d79" />

# Part 3 Configure IPv6 Inter-VLAN Routing

First step was to enable IPv6 Routing 

<img width="639" height="99" alt="image" src="https://github.com/user-attachments/assets/1528c4f2-8d39-4e70-a8f1-3c0ce59a9d71" />


Next I configured IPv6 addresses for VLAN 10, VLAN 20 and VLAN 30. 

<img width="637" height="521" alt="image" src="https://github.com/user-attachments/assets/0facb281-b038-4f04-8cad-08f819f1af07" />

After configuring VLAN IPv6 Addresses I configured G0/2 MLS interface for IPv6 address.

<img width="633" height="45" alt="image" src="https://github.com/user-attachments/assets/8e7cfa72-7d9b-4377-aede-62351287dd8a" />

Now I have configured Layer 3 Switching and Inter-LAN Routing. 
