# Cisco Packet Tracer - Implement Port Security

## Network topology 

<img width="651" height="337" alt="image" src="https://github.com/user-attachments/assets/5416527d-aac8-4ecb-91ac-43de43ca1f03" />

## Network Addressing Table

<img width="779" height="185" alt="image" src="https://github.com/user-attachments/assets/acea58ed-83c0-458d-af6e-3d6dead7b7a7" />


## Part 1 Configure Port Security 
In this Cisco Packet Tracer module I implement port security on a switch. Port security restricts port's ingress trafficc. It uses MAC adresses to verify which address is allowed to send traffic into the port. 

Switch 1 has two hosts connected to it PC1 and PC2. Both interfaces connecting these host needs to have port security. To configure port security into Cisco switch I did the following below.

I opened S1 Command Line Interface and entered to configuration mode. Port security is configured into each interface, I issued command `interface range fastEthernet 0/1 -2` and issued command `switchport port-security` to enable port security in F0/1 and F0/2 interfaces. 

Next I issued command `switchport port-security maximum 1`, this command allows only one device to access the port. Interfaces in this excersise are also configured to dynamically learn MAC addresses of devices. This can be configured with command `switchport port-security mac-address sticky` after configuring sticky address to the switch, I configured port security violation which allows different modes to be used. 

In this excersise I issued command `switchport port-security violation restrict`, it keeps the port active, drops packets from unknown MACs, and generates a log message. 

<img width="701" height="970" alt="image" src="https://github.com/user-attachments/assets/738051cb-3637-41fc-aac1-5b85d5e430a9" />

After configuring F0/1 and F0/2 interfaces, I disabled remaining interfaces to prevent connecting unauthorized devices to the switch. 
