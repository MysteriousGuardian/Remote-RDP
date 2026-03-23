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

**Hyper-V**: *When doing the original setup, my network was acting funny after creating the external switch. I did not think much of it, since I thought it was expected behavior. After the network came back up on my home PC, nothing worked. I couldn't access the internet, my pings were useless. I fixed it, by turning off the IPv4 feature on my switch.*

*However it still aroused suspicion, since I didn't have any problems since before fixing my WireGuard. Maybe the Hyper-V switch created a faulty switch? I deleted my old switch and created a fresh one with correct settings. Still no victory.*

**Firewall (Home PC)**: *I had another thought that my firewall could have blocked communications from server to my home PC, but I realized that it was impossible, since both are in the same network (HomePC had 192.168.1.50 and Server had 192.168.1.49). I didn't want to take risks, so I turned off home PC firewall and tried to send a ping. No positive results.*

I had to do a workaround, in which led me to create another peer user. This new peer user is for my home PC to connect with when I go to school for example. Before going out, I turn on VPN and wait 5 seconds for handshake. It was functional, but it definitely caused a workaround of my entire project goal.



# Reflection

Project Remote RDP taught me a lot of valuable skills. It taught me lots of technical skills, such as routing, WireGuard setup, networking and hypervisor management. However it did teach me lots of mental skills, such as problem solving, planning & designing and logical thinking. Would I do something like this again? Probably not for a while. But was it worth it? Absolutely!


Go back to start: [Start](../README.md)
