# In this excersise I configure router interfaces in Cisco Packet Traces. 

 # Topology of the network 

 <img width="988" height="340" alt="image" src="https://github.com/user-attachments/assets/ca188d9c-3c82-4271-869c-ee061ec801dd" />


# Adressing table 

<img width="756" height="348" alt="image" src="https://github.com/user-attachments/assets/f7e3adbb-eac0-46fe-a458-e4e32474f088" />

Finally I did the same for G0/1 interface. Last step was to save the configuration using the command "copy running-config starup-config" in a case if the router shutsdown or crashes. 


# Configuring IPv4 Addresses

First step was to configure IPv4 address for R1 and PC1 and PC2. 

I opened R1 CLI and configured G0/0 interface with 172.16.20.1 /25 IP address. After configuring the IP address I issued command for the link to go up with "no shutdown". After these were done I verified that the configuration and link was indeed correct. 

<img width="700" height="706" alt="image" src="https://github.com/user-attachments/assets/c6589cc1-9688-44e0-845a-7ea2cfed8519" />

<img width="659" height="173" alt="image" src="https://github.com/user-attachments/assets/e2e79ce5-0fd7-4075-88f1-628f3c2d8ec6" />

After that I opened PC1 and PC2 and configured correct IP addresses fro them. This was easy, because I would not need to use CLI. 

<img width="703" height="711" alt="image" src="https://github.com/user-attachments/assets/0b887448-4033-44b3-bc25-35a1c51118c6" />


# Configure IPv6 Addresses

Same proccess is for the Ipv6 addresses in the router. Insted of using an "ip address" -command, I will use "ipv6 address command". 

<img width="674" height="413" alt="image" src="https://github.com/user-attachments/assets/88c4c139-3465-4efa-8923-8f57a28ec144" />

Same process for the interface G0/1. 

After that I verified my IPv6 configurations and saved the configuration.

<img width="670" height="216" alt="image" src="https://github.com/user-attachments/assets/31c1c39b-e3f6-4dff-9953-04e99cca8691" />

Lastly I configured IPv6 addresses for PC3 and PC4.

<img width="700" height="710" alt="image" src="https://github.com/user-attachments/assets/798d3b28-99e4-4c36-95ea-f1bc82172873" />


# Pinging other hosts and Dual Stack Server

The last part of the excersise was to test networks connectivity. I did that with ping. 

Ping test was made from PC1 to PC2 and PC2 to Dual Stack server. 









