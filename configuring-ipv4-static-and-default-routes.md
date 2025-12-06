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

Configuring R1 router with static routes to PC2 and PC3 network. Both networks destination interface is R2 serial `172.31.1.192`

<img width="1266" height="138" alt="image" src="https://github.com/user-attachments/assets/a442e518-8d30-4217-bb3b-1d559f12cbd4" />


# Configuring Default Routes 


# Verify Connectivity 
