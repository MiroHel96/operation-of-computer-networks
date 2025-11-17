# Cisco Packet Tracer - Switch Security Configuration

## Network topology

<img width="850" height="407" alt="image" src="https://github.com/user-attachments/assets/809c2905-42f7-411c-92eb-4df3a5d25cad" />

## VLAN Table

<img width="723" height="327" alt="image" src="https://github.com/user-attachments/assets/bd097292-9e6f-44cb-93b6-f186cbca1d8c" />


# Summary 

In this packet tracer excersise I will implement security featurers to SW-1 and SW-2.  

# Part 1 Creating a Secure Trunk

I started by connecting a Straight trough cable between the switches in interfaces G0/2. Next Both interfaces were configured with trunks. 

<img width="702" height="713" alt="image" src="https://github.com/user-attachments/assets/464d089d-8466-433d-be86-3c817e200ddb" />

<img width="699" height="711" alt="image" src="https://github.com/user-attachments/assets/4664280d-da1d-4dbb-a24f-6e6d8a3399f8" />

I disabled DTP negotiation on both sides of the link. Dynami Trunking Protocol is used for autonegotiation whether a port should become an access port or a trunk port. I already configured them manually so there is no need for DTP. Disabling it also reduces attack surface for VLAN hopping. There is othe benefits, but the point is security in this excersise. 

# Part 2 Securing unused SwitchPorts

# Part 3 Implementing Port Security 

# Part 4 Confiugring PortFast, and BDUP Guard (DHCP Snnooping)

