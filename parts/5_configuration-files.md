# 5. Configuration Files

The same procedure was done as part 4, however the client comes into play. In this project, my client is a Windows 10 laptop. To configure the client side, I will need to install WireGuard VPN on Windows. From there, I can create and use my config file. By creating a new tunnel and following this template, the client side of configurations should be done: 

```
[Interface]
PrivateKey = <AutoGenerates>
ListenPort = 51820   <Optional>
Address = 192.168.2.2/24   <The IP address that the peer will receive>
DNS = 192.168.1.1   <Good to have, DNS will work if this is added>
MTU = 1380   <Speedbooster>

[Peer]
PublicKey = <WireGuard Server Public Key>
AllowedIPs = 192.168.2.0/24, 192.168.1.0/24   <Allow split-tunnels to access the VPN>
Endpoint = <Either a public IP address or a DDNS, end with :portnumber>
PersistentKeepalive = 25   <Sends keep alive packets to allow NAT to work as usual>
```

(At that point, I got so many errors when testing connectivity to my home PC, so I ended up installing another WireGuard VPN to my home PC and created another configuration with the same template. I will go a bit in depth later on.)

When the configuration files have been configurated, it is time to go back to the WireGuard Server VM and add another small addon for each client connected to WireGuard. Simply nano into the wg0.conf file and write this:

```
[Peer]
PublicKey = <The clients public key (Already displayed when creating a new tunnel).>
AllowedIPs = 192.168.2.2/32   <The IP address that the client will get. Subnet 32 is required to indicate that the provided address is the only address the client will receive.>
```

Make sure to include both the client's and the home PC's configuration. At that point, the configuration files are done!

Next part: [Router Configuration](/parts/6_router-configuration.md)

