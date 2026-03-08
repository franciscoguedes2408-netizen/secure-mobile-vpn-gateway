# Architecture

This folder contains the network architecture and diagrams
for the Secure Mobile VPN Gateway lab.
# Network Architecture

This lab simulates a secure remote access environment using a VPN gateway.

The architecture is designed to allow a mobile device to securely connect
to a private network through an encrypted tunnel using WireGuard.

## Components

Mobile Device  
Used to establish the VPN connection.

Router  
Handles port forwarding for the VPN service.

Ubuntu Server  
Acts as the VPN gateway and routes traffic to the internet.

WireGuard  
Provides encrypted VPN tunneling.

UFW Firewall  
Controls network access and restricts incoming traffic.

Fail2Ban  
Protects SSH access from brute-force attacks.

## Security Concept

The gateway follows a minimal exposure model:

- Default deny firewall policy
- Only essential ports exposed
- SSH brute-force mitigation
- Reduced network visibility
