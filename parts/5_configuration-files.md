# 5. Configuration Files

The same procedure was done as part 4, however the client comes into play. In this project, my client is a Windows 10 laptop. To configure the client side, I will need to install WireGuard VPN. From there, I can create and use my config file. By following this template, the client side of configurations should be done: 

```
[Interface]
PrivateKey = <AutoGenerates>
ListenPort = 51820   <Optional>
Address = 192.168.2.2/24   <The IP address that the peer will recieve>
DNS = 192.168.1.1   <Good to have, DNS will work if this is added>
MTU = 1380   <Speedbooster>

[Peer]
PublicKey = <WireGuard Servers Public Key>
AllowedIPs = 192.168.2.0/24, 192.168.1.0/24   <Allow split-tunnels to access the VPN>
Endpoint = <Either a public IP address or a DDNS, end with :portnumber>
PersistentKeepalive = 25   <Sends keep alive packets to allow NAT to work as usual>
```

At this point, I got so many errors when testing connectivity to my home PC, so I ended up installing another WireGuard VPN to my home PC and created another configuration with the same template. I will go a bit in depth later on.

When 
