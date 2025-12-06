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

