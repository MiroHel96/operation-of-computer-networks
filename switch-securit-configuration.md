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

<img width="635" height="76" alt="image" src="https://github.com/user-attachments/assets/a8fa89e6-c220-4c88-a6fa-0782c189447c" />

<img width="628" height="199" alt="image" src="https://github.com/user-attachments/assets/cec1ce6a-7971-4749-9673-4f4887108465" />

Next I created `VLAN 100` with the name `Native` for both switches and configured all trunk ports to use VLAN 100 as the native VLAN.

<img width="633" height="61" alt="image" src="https://github.com/user-attachments/assets/3417c22d-d0a3-4bc9-9066-12dddc484f39" />

<img width="633" height="481" alt="image" src="https://github.com/user-attachments/assets/deb770f7-3f43-47d2-886e-bc3084bd56bb" />

I encountered an issue, both switches kept sending following error `CDP-4-NATIVE_VLAN_MISMATCH: Native VLAN mismatch discovered on GigabitEthernet0/1 (1), with DLS1 GigabitEthernet1/0/1 (100).`, I needed to configure interface G0/1 with the following commands to correct the Native VLAN mismatch:
- `Switchport mode trunk`
- `Switchport trunk native vlan 100`
- `Switchport nonegotiate`

# Part 2 Securing unused SwitchPorts

In this part I shutdown all of the unused ports on SW-1.

<img width="440" height="131" alt="image" src="https://github.com/user-attachments/assets/aa47ca63-e6b9-424e-a7ba-1f05b2be6699" />

As we can see from below, all of the unused ports are `administratively down`. After shutting down all unsused ports I created a VLAN 999 named `BlackHole`, in there I moved all of the unused ports.

<img width="701" height="709" alt="image" src="https://github.com/user-attachments/assets/4e4f8b99-96cd-42c3-848f-fa16b17a63e5" />

Creating the BlackHole VLAN and assigning all unused ports to it.

<img width="632" height="74" alt="image" src="https://github.com/user-attachments/assets/a5074863-b216-4ece-8252-cbe237e2769a" />

<img width="637" height="103" alt="image" src="https://github.com/user-attachments/assets/a123c5cd-508d-48fb-86ff-4d16fee308b2" />

<img width="635" height="367" alt="image" src="https://github.com/user-attachments/assets/18b202b7-c45b-4710-8f5d-4e707a6cf639" />


# Part 3 Implementing Port Security 

# Part 4 Confiugring PortFast, and BDUP Guard (DHCP Snnooping)

