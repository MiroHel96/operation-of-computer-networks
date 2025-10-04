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




