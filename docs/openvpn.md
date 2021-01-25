# OpenVPN Information

## To Connect an Ubuntu machine to OpenVPN server

_System Info_

- Date: 2021.01.21
- OS: Ubuntu 20.04
- OpenVPN: OpenVPN 2.4.7
- Configuration File: 192.168.20.2.ovpn
  - File Location => `~/Documents/work/KBs/`

_Procedure_

- `sudo apt update`
- `sudo apt install openvpn -y`
- Download the Standalone VPN Client configuration file from your WebAccess/VPN server.
- Navigate to the directory where the configuration was downloaded.
  - For my example, it would be `cd ~/Downloads`
- Then, run the following command to the connect to the OpenVPN server.
  - `sudo openvpn --config 192.168.20.2.ovpn`