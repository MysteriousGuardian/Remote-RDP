# 2. Setup 

The only setup phase that I did, was to activate the Hyper-V feature and create a Virtual Machine for my WireGuard server. Other than that, it was mainly researching about all the components.


Hyper-V is a hypervisor that uses the hosts computer resources to power virtual machines in a centralized place. In other words, Hyper-V is the feature that lets me create and run my WireGuard server on my home computer. 

It was a piece of cake to activate the feature, you only need to search "feature" on Windows Search Bar to then get the result "Activate or Disable Windows Features". Follow the wizard and find the Hyper-V feature. 


My WireGuard server was created with these VM specifications:

| Resource | Value |
|---------|-------|
| CPU | 1 vCPU |
| Memory | 2048 MB |
| Disk | 30 GB |
| OS | Ubuntu 22.04 LTS |
| Purpose | WireGuard VPN Server |


A user was created with the name "wgserver" and after going through with the installation, updates were done. When going through with upgrade, I noticed that my VM does not have access to my network. At that point, I did some research to find out that I needed to configure an external switch to my Hyper-V.

An external switch lets me configure my network card to act like a switch and route VM traffic to my router. In simpler terms, I create an imaginary switch that connects my VM to my home network. A lot of errors happened during the process, which I will review on a later part. I managed to fix all the problems and begin my WireGuard server setup.



Next part: [DDNS](3_ddns.md)
