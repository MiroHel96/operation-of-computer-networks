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

### Password encryption and SSH 

To encrypt plaintext passwords in Cisco devices you can use command `service password-encryption` in configuration mode. 

<img width="637" height="158" alt="image" src="https://github.com/user-attachments/assets/dcd5bf84-3808-457f-8b99-c7095f3401d9" />

Next I generated user `SSHadmin` with password `55Hadm!n`. After creating the user I generated SSH key, command `crypto key generate rsa general-keys modulus 1024`. 

<img width="634" height="203" alt="image" src="https://github.com/user-attachments/assets/e1a5489e-0b8c-4c8a-8778-7179bc1f49e5" />

<img width="640" height="634" alt="image" src="https://github.com/user-attachments/assets/9d14211d-135f-48b5-88ff-aa8588db2f17" />

### Securing console and vty lines 

In this section I secure R2 console connection with password and vty lines to accept only SSH connections. 

Console

I configured console with password cisco, session to logout after 6 minutes, enabled login and to prevent console messages to interupt commands I used command logging synchronous.

<img width="636" height="1024" alt="image" src="https://github.com/user-attachments/assets/d70b5c8d-3f88-4b1f-8fac-c798acc94725" />

SSH connection 

I configured vty lines 0-15 to accept only ssh connection, logout timeout to 6 minutes, password cisco and enabled login with local database. 

<img width="631" height="468" alt="image" src="https://github.com/user-attachments/assets/4ed9aa0f-cf94-42a0-9a76-5cc093f8acd1" />

Next I generated banner `Unauthorized access is prohibited`, using `banner motd` -command in configuration menu.

<img width="644" height="123" alt="image" src="https://github.com/user-attachments/assets/1e5b2eac-dc0a-453e-ba78-cff11bbed8e7" />

### Enabling IPv6 routing and configuring interfaces with IP addresses

To configure IPv6 routing in Cisco router you must use following command in configuration mode `ipv6 unicast-routing`. The following command enables IPv6 routing globally on your router. 

Enabling routing in Cisco device

<img width="639" height="209" alt="image" src="https://github.com/user-attachments/assets/b24a676f-9f41-4bd1-a139-fb9509a19ee9" />

Verifying that routing is enabled 

<img width="637" height="511" alt="image" src="https://github.com/user-attachments/assets/55990a7c-942e-44e4-ab8f-124f4e5a7a5a" />

After routing is enabled globally I configured each connected interface with IPv4 and Ipv6 addresses. I configured two GigibitEthernet and two Serial interfaces with the following IP addresses and issued `no shutdownb` command to each interface to turn on the link. 

Interfaces configured:
- `G0/0/0` 2001:db8:acad:4::1 /64 
- `G0/0/1` 2001:db8:acad:5::1 /64 
- `S0/1/0` 2001:db8:acad:3::2 /64 
- `S0/1/1` 2001:db8:feed:224::1/64 

### IPv6 configuration
<img width="633" height="1005" alt="image" src="https://github.com/user-attachments/assets/783e0886-92a9-4f72-bb9a-ffca67d985b8" />

Verification of interfaces `show ipv6 interface brief`

<img width="475" height="218" alt="image" src="https://github.com/user-attachments/assets/9bb414ba-d149-46bd-8fd7-bb466079235c" />


### IPv4 configuration

Configuation of IPv4 addresses were the following: 
- `G0/0/0` 10.0.4.1 /24
- `G0/0/1` 10.0.5.1 /24
- `S0/1/0` 10.0.3.2 /24
- `S0/1/1` 209.165.200.225 /30


<img width="632" height="367" alt="image" src="https://github.com/user-attachments/assets/d7789fd2-ac15-4cb0-b270-6438dd6327b7" />

Verification of IPv4 interfaces 

<img width="635" height="114" alt="image" src="https://github.com/user-attachments/assets/dfeeb2d9-b0b4-4a10-a225-a69b81a8da2d" />

### Verifying network connectivity 

After configuration of R2 I verfied that each host could communicate between networks to test if routing works.


## Part 2 Displaying router information 
