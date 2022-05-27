# WireGuard

* free and open-source communication protocol and software which implements encrypted virtual private networks (VPNs)
* passes traffic over UDP

## WireGuard & Advantech Routers

* Up to 4 WireGuard VPN tunnels per router

### Windows 10 Client to ICR-3241 (Client-to-Server)

#### ICR-3241 Configuration (Server)
* Fields to update:
    - Description
    - Local Port 
    - NAT/Firewall Traversal
    - Interface IPv4 Address
    - Interface IPv4 Prefix Length
    - Install Routers
    - Traffic Selector
    - Remote Subnets
* Click on the __Generate__ box to generate a Local Private Key and a Local Public Key
* Copy and paste the Remote Public Key from the Windows 10 WireGuard Client
* Click Apply

#### Windows 10 Configuration (Client)
* Click Add Empty Tunnel in the WireGuard Software
* In the __Create New Tunnel__ window, do the following:
    - Give your tunnel a name
    - Copy the public and private keys to a safe location
    - Below `[Interface]` and `Private Key`, enter the following:
        - the VPN IP address you want to give the Windows client
        - the DNS address
* Please see example below
```yaml
[Interface]
PrivateKey = <removed>
Address = 172.16.24.1/32
DNS = 8.8.8.8, 8.8.4.4
```
* Now you will need to enter the configuration information for the peer, in this case server.
* Please see example below
```yaml
[Peer]
PublicKey = <removed>
AllowedIPs = 192.168.20.0/24 # The network behind the router
Endpoint = <publicly_accessible_IP>:51820
```
