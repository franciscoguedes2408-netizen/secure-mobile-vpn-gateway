# Server Setup

Documentation of the Ubuntu Server installation
and WireGuard VPN configuration.
# Server Setup

This section documents the installation and configuration of the VPN gateway server.

## Environment

Ubuntu Server running in a virtualized environment.

## Installation Steps

Update the system:

sudo apt update
sudo apt upgrade -y

Install required packages:

sudo apt install wireguard ufw fail2ban

Enable IP forwarding:

Edit the file:

/etc/sysctl.conf

Add the following line:

net.ipv4.ip_forward=1

This allows the server to route VPN traffic to the internet.
