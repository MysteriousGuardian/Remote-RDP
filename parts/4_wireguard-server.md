# 4. WireGuard Server

After our DDNS situation has been completed, it's time to fix our WireGuard VPN Server that will act as our "receptionist". From our setup, we got this enviorment to work with:

<img src="/assets/bild4-1.png">


We start off by installing WireGuard using Terminal:

```
sudo apt update
sudo apt install wireguard
```

Now we create two seperate keys for the server to act as an authentication agent. A public key is used to send encrypted traffic and verify who the information was sent by. A private key is the method used to open the information sent over. Public keys are meant to leave the device, while the private key is meant to never leave the device. By writing this command, the public and private key will be generated and saved in corresponding files:

```
wg genkey | tee server_private.key | wg pubkey > server_public.key
```

We can verify that these keys are created:

```
cat server_private.key
cat server_public.key
```

Now we start by creating a configuration file for the server by using: 

```
sudo nano /etc/wireguard/wg0.conf
```

It's important to run nano as root, since the wg0.conf file does not exist, we simply create a new one. Linux doesn't like when regular users create files on WireGuard directory, so a simple fix was running nano again as root. When inside nano, simply paste the config template:

```
[Interface]
Address = 10.0.0.1/24        # VPN subnet
ListenPort = 51820
PrivateKey = <server_private_key>

# Enable NAT and routing (will cover next)
PostUp = iptables -A FORWARD -i %i -j ACCEPT; iptables -A FORWARD -o %i -j ACCEPT; iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
PostDown = iptables -D FORWARD -i %i -j ACCEPT; iptables -D FORWARD -o %i -j ACCEPT; iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE
```

Something to note, the address used on this project was not on the same LAN as my actual network, since it required extra tinkering with Layer 2, which would be a risky move. I decided to utilize the 192.168.2.0/24 network, since it was not used for anything. By rewriting the address part of the template and adding my private key, the configuration for the server was basically done.

However we have to enable IP forwarding. This setting allows us to communicate beyond our network, for example the internet. To activate the setting, simply write these two commands:

```
echo "net.ipv4.ip_forward=1" | sudo tee -a /etc/sysctl.conf
sudo sysctl -p
```
I will be adding more, since part 5 will require more config from the server.

Next
