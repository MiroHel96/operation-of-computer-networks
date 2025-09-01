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



After that I verified my VLAN configurations.


<img width="702" height="713" alt="image" src="https://github.com/user-attachments/assets/67bfff39-c115-4e25-ad37-bd38ca1740e4" />


