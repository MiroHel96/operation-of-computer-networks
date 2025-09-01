# Cisco Packet Tracer VLAN Configuration

In this module I configure VLANs in cisco packet tracer excersise. 

Topology of the network
<img width="802" height="413" alt="image" src="https://github.com/user-attachments/assets/68181a51-cd01-4544-a3cb-96a2697a12d4" />

Addressing Table

<img width="849" height="233" alt="image" src="https://github.com/user-attachments/assets/d3b168a8-1dd1-47b1-b6bb-aeebf2ba4c17" />


# Objective 1 Display the current VLANs

I opened S1 Comandline interface and issued the following command to see current VLAN infomration. 
 - show vlan brief

As we can see, currently there is no other VLANs than VLAN1.

<img width="705" height="708" alt="image" src="https://github.com/user-attachments/assets/470ad666-9338-4d80-a992-7fd12b00332b" />

After that I pinged each PC with other host in the same subnet. I got a reply from each as expected.

<img width="699" height="711" alt="image" src="https://github.com/user-attachments/assets/f8696d6b-e5df-4943-8b7b-f7d848709803" />




# Objective 2 Configure VLANs

I opened S1 CLI and configured the following VLANs and Names for them.

-  VLAN 20: Students
-  VLAN 30: Guest(Default)
-  VLAN 99: Management&Native
-   VLAN 150: VOICE

<img width="699" height="712" alt="image" src="https://github.com/user-attachments/assets/4fb53e2d-e069-4823-9ea2-0397d8af4f60" />



After that I verified my VLAN configurations and saved my configuration to the switch with command "copy running-config startup-config".


<img width="702" height="713" alt="image" src="https://github.com/user-attachments/assets/67bfff39-c115-4e25-ad37-bd38ca1740e4" />

After configuring S1 I did the same configurations for the S2 and S3.


# Objective 3 Assign VLANs to the active ports. 

After I have configured VLANs for each switch I must then configure each individual VLAN to correct interface.

I opened S1 and entered the following commands. 
- interface id
- switchport mode access
- switchport access vlan id


S2
 VLANs which I configured with the following names:
 -  VLAN 10: FastEthernet 0/11
 -  VLAN 20: FastEthernet 0/18
 -   VLAN 30: FastEthernet 0/6


S3
 VLANs which I configured with the following names:
 -  VLAN 10: FastEthernet 0/11
 -  VLAN 20: FastEthernet 0/18
 -   VLAN 30: FastEthernet 0/6


<img width="699" height="711" alt="image" src="https://github.com/user-attachments/assets/0c092705-2e2b-4365-8cd5-9e0060e86b4c" />

<img width="704" height="718" alt="image" src="https://github.com/user-attachments/assets/4733cbff-4014-4c99-a57a-722bfc304e2b" />

Finally I configured the S3 FastEthernet 0/11 interface with voice vlan. 

<img width="700" height="716" alt="image" src="https://github.com/user-attachments/assets/d9f647e8-661a-44ea-8d2f-c63599b85791" />


# Bonus Trunk mode for S1

I configure trunk port for S1 


<img width="702" height="783" alt="image" src="https://github.com/user-attachments/assets/c8d00317-fbb7-4040-88f9-4fbab97f76dc" />

<img width="635" height="290" alt="image" src="https://github.com/user-attachments/assets/456c9b08-8c5d-4eda-b7e9-45ca329f2b6b" />


Switch 2 trunkport information 
<img width="705" height="714" alt="image" src="https://github.com/user-attachments/assets/fa16e46e-3ce0-40e4-8cef-784def826e90" />


