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
