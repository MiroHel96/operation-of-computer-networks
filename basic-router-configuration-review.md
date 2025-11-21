# Cisco Packet Tracer Basic Router Configuration Review


## Network Topology 

<img width="932" height="494" alt="image" src="https://github.com/user-attachments/assets/c3311940-f06d-454e-bcca-75feae8e3554" />

## Addressing Table 

<img width="863" height="568" alt="image" src="https://github.com/user-attachments/assets/7240e3f8-f014-4fa2-a3e2-332f035bfc22" />


## Part 1 Configuring router

In step 1 I had to configure PC3 and PC4 IP addresses according to the addressing table, after configuring IP addresses for the PC's I continued to configure basic router settings for R2.

PC3 IP addresses the same was done for PC4 according to the IP table. 
<img width="701" height="715" alt="image" src="https://github.com/user-attachments/assets/cdc3b170-05e7-45f9-aef5-118652e33d99" />


### Configuring router settings 

In this part I configure basic settings for R2. First step was to configure hostname for the router, to configure hostname for the router I entered to privileged EXEC mode and from there to configuration mode. Command `hostname` is used to set the hostname of the device.

<img width="635" height="130" alt="image" src="https://github.com/user-attachments/assets/4a4bc0a0-5484-47e1-a236-6929c8c6e2c5" />

Next I configured encrypted password for privileged EXEC mode. To configure privileged EXEC mode encrypted password I issued command `enable secret` and after that password c1sco1234. I verified that the password is encrypted from the running configuration with the command `show running-configuration`. 

<img width="637" height="227" alt="image" src="https://github.com/user-attachments/assets/1eb31589-eaaa-41ad-a539-c7ff01cc3738" />

As shown below the privileged EXEC mode password is encrypted 

<img width="632" height="344" alt="image" src="https://github.com/user-attachments/assets/19e76403-9d3b-4d0a-bcd1-222d041bc2cd" />

Next step was to configure domain name and disabling DNS lookup for the router. DNS lookup is disabled to prevent it from attempting to translate incorrect commands and typos as host names. 

The following commands were used below: 
- `ip domain-name` - ccna-lab.com
- `no ip domain-lookup` - to disable domain-lookup from incorrect commands/typos

<img width="635" height="452" alt="image" src="https://github.com/user-attachments/assets/7a8c6125-c8df-4fcb-b3e9-f5ed922d5a55" />

Next I saved the configuration to keep the changes. 

`copy running-config startup-config`
<img width="637" height="115" alt="image" src="https://github.com/user-attachments/assets/40ca7736-c6a4-4dc4-ac1a-b99918662c2e" />

## Part 2 Displaying router information 
