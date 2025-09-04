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


