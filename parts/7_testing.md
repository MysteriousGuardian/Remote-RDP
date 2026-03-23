# 7. Testing

Alright time to test our VPN. I started by writing this command on the server terminal:

```
sudo wg-quick up wg0
```

Then it is time to turn on WireGuard VPN for both the home PC and the client. To mimic remote distance, I've connected my client to my mobile hotspot instead of LAN. After turning both of the VPNs on, I instantly survellianced the WireGuard logs for both home PC and the client. The reasoning behind it, is to see if a keypair has been created between the peer and the server. In our situation, both peers got their own keypair and they both are officially in a seperate LAN connected to my home network. 

I wanted to try pinging my home PC from my client, but I noticed that my network speed was awful. In some cases, the connection were lost. I would have to accept the fact that my setup wouldn't be fast, since I've utilized a virtual machine instead of a seperate mini-server, which is horrible and my home PC specifications are not sufficient enough to improve speed.

Anyhow, I simply opened up RDP to connect to home PCs virtual IP, which is 192.168.2.2. By authenticating myself and accepting the insecure certificate, I managed to open up a remote session on my actual home PC, while not being on my own network: 



