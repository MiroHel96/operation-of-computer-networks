# Cisco Packet Tracer - Configuring IPv4 Static and Default Routes

## Network Topology

<img width="1290" height="734" alt="image" src="https://github.com/user-attachments/assets/594eb2e1-a7a9-4f6f-b673-e1a584e815ab" />

## Addressing Table 

<img width="1176" height="708" alt="image" src="https://github.com/user-attachments/assets/15155935-3986-4657-81b5-5f9478cdf305" />

# Configuring Static Routes 

I had to configure static routes from PC2 network to PC3. Static routes need configuration to both ways of the network if I only configure how R1 and R2 can reach destination network they don't still know how to send it back. 

R2 configuring static route to `172.31.1.128/26` network. Using command `ip route destination network, subnetmask, interface.`

<img width="1274" height="132" alt="image" src="https://github.com/user-attachments/assets/9ec8f28e-9c24-4550-9058-961f2b38fe83" />

R3 configuring static route to `172.31.0.0/24` network.

<img width="1266" height="84" alt="image" src="https://github.com/user-attachments/assets/42db8f32-c381-48cb-8ae1-61235ebdfc4c" />

Configuring R1 router with static routes to PC2 and PC3 network. Both networks destination interface is R2 serial `172.31.1.192`. I also had to configure static route to WAN between R2 and R3 with the IP address of `172.31.1.196/30`. 

<img width="1268" height="344" alt="image" src="https://github.com/user-attachments/assets/ffc74092-45e4-466a-a2a4-c48a55bd36e5" />

As we can see from the picture below, now we have configured 3 static routers to 3 different networks. 

<img width="1294" height="556" alt="image" src="https://github.com/user-attachments/assets/a0a399b1-98a1-44d4-93bf-5f2a7e319506" />

Next I configured directly connected route from R2 to R1 and R3 

<img width="1206" height="132" alt="image" src="https://github.com/user-attachments/assets/67b2709d-b671-46ed-9d21-760b23b90914" />

# Configuring Default Routes 

Finally I had to configure default static route for R3. I used the following command to create it `ip route 0.0.0.0 0.0.0.0 serial0/0/1`. I have now configure default static route which is "catch-all" route it is a route used by a router if nothing else does not match it's routing table, If there is not defautlt route the packet is dropped. 

<img width="1286" height="710" alt="image" src="https://github.com/user-attachments/assets/a60631d0-125f-446b-975c-f2aab0497f52" />



# Verify Connectivity 

Finally I tested each PC's connectivity between eachother with `tracert` and `ping` commands. 

Ping test from PC1 to PC2 and PC3 

<img width="1390" height="1412" alt="image" src="https://github.com/user-attachments/assets/9c3693a3-4e19-407d-afb6-b2e57dde8d25" />

Traceroute from PC1 to PC2 and PC3

<img width="1254" height="582" alt="image" src="https://github.com/user-attachments/assets/ce9b140c-509e-4ef2-a4f0-99d92e6cc2e4" />

 Ping test from PC2 to PC1 and PC3 

 <img width="1262" height="768" alt="image" src="https://github.com/user-attachments/assets/fd24d536-71a8-429a-8081-28cbcf96b4b9" />

Traceroute from PC2 to PC1 and PC3 

<img width="1262" height="556" alt="image" src="https://github.com/user-attachments/assets/6a968979-f9e5-457e-a30e-35293c607577" />

Ping test from PC3 to PC2 and PC1 

<img width="1288" height="842" alt="image" src="https://github.com/user-attachments/assets/b0c7b860-0aa4-4b09-b7b8-5abbd31277a4" />

Traceroute from PC3 to PC2 and PC1 

<img width="1258" height="580" alt="image" src="https://github.com/user-attachments/assets/2766d5df-4f3a-4121-af40-c045df6b125c" />

Aswe can see ping and traceroute tests were success and I can now conclude that all of the hosts in my network can communicate with eachother. 
