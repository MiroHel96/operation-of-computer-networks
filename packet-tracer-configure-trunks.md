# Cisco Packet Tracer Configure Trunks

In this excersise I configure trunkports for VLANs.

Topology of the excersise.

<img width="773" height="364" alt="image" src="https://github.com/user-attachments/assets/d8b7e63a-86f6-4431-aa69-f23e2b4033c0" />

Addressing Table for the excersise.
<img width="819" height="230" alt="image" src="https://github.com/user-attachments/assets/c62789e2-9ba9-476a-9d3f-2d5458e16996" />


# Objective 1 Verify VLANs

I started this excersise with displaying S1, S2 and S3 VLANs.
Using command "show vlan brief", I could see the current VLANs of the device.

<img width="701" height="707" alt="image" src="https://github.com/user-attachments/assets/c608facd-6111-48eb-ad83-f08cfbaff1c6" />

I did the same for S2 and S3 and verified that the VLANs are configured according to the Addressing Table.

<img width="704" height="703" alt="image" src="https://github.com/user-attachments/assets/183d5456-18b8-4d22-8ffa-b44ed1f8e3ac" />

<img width="699" height="711" alt="image" src="https://github.com/user-attachments/assets/e283fa80-ee6e-43bf-9dc7-f06c45bb418b" />


# Objective 2 Configure Trunks

After verifying VLANs and correct interfaces I configured trunk ports for S1. 
Selected the correct interface "interface GigabitEthernet 0/1" and issued command "switchport mode trunk". I could have done both ports simultaneously using command "interface range".

<img width="699" height="714" alt="image" src="https://github.com/user-attachments/assets/65ed0ba2-de16-402a-aed8-e3778bc5a6e7" />

I also configured VLAN 99 as the native VLAN for G0/1 and G0/2 interfaces on S1.

<img width="644" height="114" alt="image" src="https://github.com/user-attachments/assets/3a8516e1-a5a0-4c42-bd28-c7a4df72f4e8" />

There is a mismatch with VLAN in the network but the ping still works, why? I configured S1 with native VLAN 99, S2 and S3 are configured with native VLAN 1. The ping is successful because devices are using accessports which use VLAN tagging. Accesports VLAN tags are not affected when they move to trunk port in switch. Native VLAN only affects to traffic which is untagged. 


I configured S2 and S3 trunkports with the correct native vlan, which is 99. Finally I save the configuration to all of the switches. 

<img width="645" height="255" alt="image" src="https://github.com/user-attachments/assets/84191058-a369-426f-b892-9cfe09ef1548" />


<img width="648" height="314" alt="image" src="https://github.com/user-attachments/assets/43720d8b-1329-4f74-89b2-6e765f7209c3" />




