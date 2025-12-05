# Cisco Packet Tracer - Implement Port Security

## Network topology 

<img width="651" height="337" alt="image" src="https://github.com/user-attachments/assets/5416527d-aac8-4ecb-91ac-43de43ca1f03" />

## Network Addressing Table

<img width="779" height="185" alt="image" src="https://github.com/user-attachments/assets/acea58ed-83c0-458d-af6e-3d6dead7b7a7" />


## Part 1 Configure Port Security 
In this Cisco Packet Tracer module I implement port security on a switch. Port security restricts port's ingress traffic. It uses MAC adresses to verify which address is allowed to send traffic into the port. 

Switch 1 has two hosts connected to it PC1 and PC2. Both interfaces connecting these host needs to have port security. To configure port security into Cisco switch I did the following below.

I opened S1 Command Line Interface and entered to configuration mode. Port security is configured into each interface, I issued command `interface range fastEthernet 0/1 -2` and issued command `switchport port-security` to enable port security in F0/1 and F0/2 interfaces. 

Next I issued command `switchport port-security maximum 1`, this command allows only one device to access the port. Interfaces in this excersise are also configured to dynamically learn MAC addresses of devices. This can be configured with command `switchport port-security mac-address sticky` after configuring sticky address to the switch, I configured port security violation which allows different modes to be used. 

In this excersise I issued command `switchport port-security violation restrict`, it keeps the port active, drops packets from unknown MACs, and generates a log message. 

<img width="701" height="970" alt="image" src="https://github.com/user-attachments/assets/738051cb-3637-41fc-aac1-5b85d5e430a9" />

After configuring F0/1 and F0/2 interfaces, I disabled remaining interfaces to prevent connecting unauthorized devices to the switch. I used the following commands `interface range f0/3 - 24, g0/1 - 2` and `shutdown` to disable rest of the ports.

<img width="677" height="766" alt="image" src="https://github.com/user-attachments/assets/442afdc5-3054-4aae-bd2a-602608d97a5f" />

After disablin rest of the ports I did a ping test from PC1 to PC2, to verify port security is enabled. PC1 and PC2 should now be in the running configuration, which I verified with the command `show run | begin interface`. As we can see from the snapshot below, port security is enabled in interface F0/1 and F0/2. 

<img width="703" height="712" alt="image" src="https://github.com/user-attachments/assets/a39c6aa0-30ed-4fec-9897-1ac16ff29939" />

With the command `show port-security`, CLI displays the current port security settings and statistics for all interfaces. 

<img width="621" height="156" alt="image" src="https://github.com/user-attachments/assets/4a8d56a0-c0a7-4b85-8230-7d9055b15bc8" />

Command `show port-security address`, displays secure MAC addresses that have been learned or manually configured on switch ports. It's more detailed view than `show port-security`.

<img width="614" height="98" alt="image" src="https://github.com/user-attachments/assets/81cc7887-a511-403c-be22-bc0556124f06" />

Next I connected Rogue Laptop to fastEthernet0/3, the interface is disabled so I had to enable it with `no shutdown` command.

<img width="700" height="1085" alt="image" src="https://github.com/user-attachments/assets/050f0c24-2bc7-4ce1-b8ef-5543a65ea5cd" />

Next I pinged PC1 from the Rogue Laptop and as we can see from below I got response. I removed PC2 from F0/2 interface and connected Rogue Laptop to it. Ping test was not anymore successfull as I have already enabled port security into the interace. 

<img width="693" height="708" alt="image" src="https://github.com/user-attachments/assets/c8cc47ea-7cc3-44c8-90a4-9de893a64738" />

Verifcation of fastEthernet0/2 ports security can be done with the command `show port-security interface f0/2`. As we can see we have 5 violations, one from connecting the device to the port and four from the ping test. (ICMP messages include unauthorized MAC address).

<img width="613" height="268" alt="image" src="https://github.com/user-attachments/assets/eeeb217f-0b6b-463c-97a8-c2fcbdfb1a52" />

Now I have implemented basic port securify. 
