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

Next I had to configure R2 as a DHCP Client. 

R2 need to receive it's IP address from the ISP. 

I used the following commands to make R2 as a DHCP Client: 
- `interface g0/1`, the interface which goes to the internet and to ISP. 
- `ip address dhcp`, This command assumes ISP is configured to provided customers with IPV4 addressing information.
- `no shutdown`

<img width="635" height="344" alt="image" src="https://github.com/user-attachments/assets/c24c9140-bd79-4e91-86e4-d0ed3504d917" />

## Verify DHCP and connectivity 

Command `show ip dhcp binding` displays a list of all
IPv4 address to MAC address bindings that have been provided by the DHCPv4 service

<img width="632" height="132" alt="image" src="https://github.com/user-attachments/assets/57fb4e8d-501b-4ede-bd6e-a049bdea804d" />

Finaly I tried to ping `www.cisco.com` from PC1 and DNS Server from PC2 to verify network connectivity.

PC1 

<img width="704" height="715" alt="image" src="https://github.com/user-attachments/assets/167f0ce6-fdbe-4b86-878e-03dd26b4249c" />


PC2 

<img width="701" height="709" alt="image" src="https://github.com/user-attachments/assets/2d60048a-6497-40bf-b354-c1aa34e12c5c" />



