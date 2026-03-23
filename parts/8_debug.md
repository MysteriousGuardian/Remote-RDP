# 8. Debug

Here are the errors and issues that I've received during my project:

# Issue 1: WireGuard handshake not working

The client couldn't connect to the server at all. Not even being able to ping the server. By doing further research, I found out that my portforwarder was on TCP, when it should have been UDP. A simple fix in the router settings made the handshake work like a charm!

# Issue 2: Routing was messed up

After solving issue 1, I still couldn't reach anyone on my network, not even beyond the network such as Google. I had a look around and saw that my AllowedIPs on my client was set to 0.0.0.0/0, in which lead to everything flowing through the VPN. If I were to have a supercomputer, it would not be a big deal. However the amount of traffic that came into the tunnel, my connections were so slowed that nothing came through. 

I changed the peers AllowedIPs to allow both the home LAN (192.168.1.0/24) and the VPN LAN (192.168.2.0/24). After the change and server restart, I could reach stuff on my network.

# Issue 3: Server can't communicate with Home PC

This might have been the biggest issue I have encountered during this project. So basically, I could ping my server from my home PC, but I couldn't do vice versa. It was strange, since I assumed that pinging from one point to another would be enough to test. 

To try to solve this issue, I created three possible causes and interrogated each one:

**Routing**: *This was my biggest suspicion, since I have that feeling that the routing must have been messed up. It could have been WireGuard during the configuration phase. It could have been Linux being a dumbnut and doing things differently than what I wanted. Hell, it could have been me, I was after all the developer.*

*By doing tests and few restorations, it still couldn't communicate. I surrendered to dive deeper on the routing part, since everything did look right to me. I dove down to cause 2.*

**Hyper-V**

**Firewall (Home PC)**
