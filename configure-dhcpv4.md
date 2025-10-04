# Cisco Packet Tracer - Configure DHCPv4

## Network topology

<img width="767" height="421" alt="image" src="https://github.com/user-attachments/assets/d911eefe-f2a8-41eb-8cf6-dca8d66523d8" />


## Addressing Table 

<img width="711" height="354" alt="image" src="https://github.com/user-attachments/assets/2bd5f0d6-ec0b-4d2f-ad09-9a76a003a359" />

## Configure a Router as a DHCP Server 

In my network topology I have R1 and R3 under R2. I had to exclude their IP Address range in R2 so there will not be duplicate IP addresses. These excluded 1 + 9 addressses will be used for static assigment of devices. 

I used command `ip dhcp exclude-address 192.168.10.1 192.168.10.10` and `ip dhcp exclude-address 192.168.30.1 192.168.30.10` in R2 Privileged EXEC configuration mode.


<img width="638" height="444" alt="image" src="https://github.com/user-attachments/assets/a07d66f4-a19e-4c88-b5aa-4cd21c24e847" />

<img width="633" height="60" alt="image" src="https://github.com/user-attachments/assets/a20e6cfa-f743-4a87-bce7-29668ee741c2" />

After excluding IP addresses I configured DHCP pools for R1 LAN and R3 LAN on R2 commandline.

I used the following commands: 
- `ip dhcp pool R1-LAN`
- `network 192.168.10.0 255.255.255.0`
- `default-router 192.168.10.1`
- `dns-server 192.168.20.254`

I used the same commands for R3 LAN but used correct addresses from the addressing table.

<img width="634" height="141" alt="image" src="https://github.com/user-attachments/assets/8d9409f3-05cd-428b-b8fc-652bd8db7b62" />

<img width="634" height="75" alt="image" src="https://github.com/user-attachments/assets/89ed2f3f-68d6-43d7-b833-b7acb3fc9d82" />


## Configure DHCP Relay 

As we can see R1 and R3 are in different subnet than R2. Therefore I have to configure Interfaces which are connected to R1 and R3 from R2 I have to configure them with helper IP addresses. After configuration R1 and R3 will act ass DHCP relay agents and they will forwatd DHCPv4 messages to other subnets. 

I used command `ip helper-address` on R1 and R3 GigabitEthernet 0/0 interfaces.

<img width="635" height="182" alt="image" src="https://github.com/user-attachments/assets/b4658842-9920-41e6-aa99-adc6e1d31457" />

<img width="614" height="202" alt="image" src="https://github.com/user-attachments/assets/1362ae73-118d-45ec-ae8e-adf63f6261ad" />

After configuring R1 and R3 I had to change PC1 and PC2 to receive their IP addresses by using DHCP. 

<img width="1400" height="704" alt="image" src="https://github.com/user-attachments/assets/74ba9a3e-9ff5-42ed-9456-b61cfc361326" />

## Configure a Router as a DHCP Client



