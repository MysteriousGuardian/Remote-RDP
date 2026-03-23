# 8. Debug

Here are the errors and issues that I've received during my project:

# Issue 1: WireGuard Handshake not Working

The client couldn't connect to the server at all. Not even being able to ping the server. By doing further research, I found out that my portforwarder was on TCP, when it should have been UDP. A simple fix in the router settings made the handshake work like a charm!

# Issue 2: LAN

# Issue 3: WireGuard Server can't communicate with Home PC
