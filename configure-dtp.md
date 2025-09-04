# Cisco Packet Tracer - Configure DTP 

In this excersise I configure VLANs and Trunk ports for switches. 

Network Topology.
<img width="668" height="332" alt="image" src="https://github.com/user-attachments/assets/ae6026ad-0da5-4092-bf2e-4e99a19da2d4" />

Addressing Table for the network. 

<img width="795" height="313" alt="image" src="https://github.com/user-attachments/assets/10b5e377-fef2-4554-9ac1-ac547396d22b" />

## Part 1 Verify VLAN Configurations. 

First I opened CLI for each switch in the network and checked their VLAN infomration. 
I used command "show vlan brief"

Switch 1
<img width="636" height="330" alt="image" src="https://github.com/user-attachments/assets/c50b7a7f-5c10-49c2-8594-264478166379" />

Switch 2
<img width="634" height="226" alt="image" src="https://github.com/user-attachments/assets/259fea0e-9578-4d90-b24a-d7cd97e29353" />


Switch 3
<img width="632" height="257" alt="image" src="https://github.com/user-attachments/assets/37ed1f95-e13e-4476-b623-a30f449dd0d2" />

Each switch had VLANs configured for the following:
 - 99 Management
 - 999 Native
 - 1002 fddi-default
 - 1003 token-ring-default
 - 1004 fddinet-default
 - 1005 trnet-default

   None of the VLANs had any interfaces configured to them.

## Part creating additional VLANs on S2 and S3

I created three different VLANs for all of the switches:
 - 10 Red
 - 20 Blue
 - 30 Yellow

<img width="692" height="121" alt="image" src="https://github.com/user-attachments/assets/bae102ee-4601-47e4-ae66-5846a9bf7502" />


I used the following commands for eachh of the switch:
 - (config) vlan id
 - (config-vlan) name - color

S2 as an example
   <img width="630" height="208" alt="image" src="https://github.com/user-attachments/assets/ebe9123c-29f0-4644-9716-bbd9404f572d" />

After configuring the correct VLANs I verified them using command show vlan brief in the privilileged EXEC mode.

<img width="627" height="296" alt="image" src="https://github.com/user-attachments/assets/f97ecd01-4cd1-46d6-a4f2-d9a371b28490" />

## Assign VLANs to Ports 

After creating VLANs I had to assign them to correct interfaces/ports.

Table for the interfaces and ports.
<img width="709" height="177" alt="image" src="https://github.com/user-attachments/assets/43e07a12-a19a-49e9-aa3b-7a7570a12e0d" />

I opened S2 CLI and entered configuation mode. I used following command to assign VLANs ports:
 - interface range f0/1-8, allows to configure multiple ports at the same time.
 - switchport mode access, makes the port to access port used for host etc.
 - switchport access vlan 10, identifies which vlan to assigns the settings.

S2 configurations
<img width="700" height="713" alt="image" src="https://github.com/user-attachments/assets/9af1cabf-55e7-41f9-8c54-0df367958e00" />


S3 Configurations 
<img width="702" height="711" alt="image" src="https://github.com/user-attachments/assets/f94cdeea-8e9b-4388-a5a3-28451f58413f" />


After configuration I save the configurations using command "copy running-config startup-config". Finally I did a ping test from PC1 to PC6 to test if the connection works. It did not, so the problem most likely is that I have not configured trunk prots for S1,S2 and S3. 


<img width="702" height="711" alt="image" src="https://github.com/user-attachments/assets/4df158b3-bc10-48d8-9bf7-a0c638c665fc" />




