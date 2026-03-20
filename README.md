# Secure Mobile VPN Gateway Lab

## Overview

This project demonstrates the deployment of a secure mobile VPN gateway using WireGuard on Ubuntu Server.

The objective of the lab is to simulate a secure remote access infrastructure with firewall hardening and protection against brute-force attacks.

The VPN gateway allows mobile devices to securely access the network through an encrypted tunnel while minimizing the exposed attack surface.

---

## Architecture

```mermaid
graph TD
    A[Mobile Device] -->|Encrypted Tunnel UDP 51820| B[Router]
    B -->|Port Forwarding| C[Ubuntu Server]

    subgraph Secure Gateway
        C --> D[WireGuard VPN Interface]
        D --> E[UFW Firewall]
        E --> F[Fail2Ban Protection]
    end

    C --> G[Internet Access]
```

---

## Technologies Used

- Ubuntu Server
- WireGuard VPN
- UFW Firewall
- Fail2Ban
- NAT / IP Forwarding
- VirtualBox

---

## Security Features

• Encrypted VPN tunnel using WireGuard  
• Firewall configured with **default deny policy**  
• SSH brute-force protection using Fail2Ban  
• Reduced host visibility by restricting ICMP echo responses  
• Minimal exposed attack surface  

---

## Project Structure

architecture/ → Network diagrams and architecture documentation  

setup/ → Server installation and WireGuard configuration  

security/ → Firewall rules and Fail2Ban configuration  

screenshots/ → Evidence of the lab running  

roadmap/ → Future improvements and expansion plans  

---

## How to Run

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/secure-mobile-vpn-gateway.git
```

Install required packages:

```bash
sudo apt update
sudo apt install wireguard ufw fail2ban
```

Enable IP forwarding:

```bash
sudo nano /etc/sysctl.conf
```

Add:

```
net.ipv4.ip_forward=1
```

Configure NAT rules in:

```
/etc/ufw/before.rules
```

Start the WireGuard interface:

```bash
sudo wg-quick up wg0
```

Verify the VPN status:

```bash
sudo wg show
```

---

## Screenshots

### WireGuard VPN Active
<p align="center">
  <img src="screenshots/wireguard-active.png" width="600"/>
</p>

### Firewall Configuration
<p align="center">
  <img src="screenshots/ufw-firewall-rules.png" width="600"/>
</p>

### Fail2Ban Protection
<p align="center">
  <img src="screenshots/fail2ban-status.png" width="600"/>
</p>

### Mobile VPN Connection
<p align="center">
  <img src="screenshots/mobile-vpn-connected.png" width="300"/>
</p>

---

## Project Status

Phase 1 – Local Lab Deployment

The current version of the project demonstrates a functional VPN gateway running in a virtualized environment with security hardening applied.

---

## Future Improvements

Planned next steps include expanding the infrastructure to simulate a production environment:

- Cloud deployment of the VPN gateway
- IDS integration using Suricata
- Honeypot deployment for attack observation
- Centralized log monitoring with Wazuh
- Network segmentation using pfSense firewall

---
## Notes

During testing, full tunnel routing (0.0.0.0/0) introduced performance limitations due to running in a local virtualized environment.

This reflects real-world constraints when deploying VPN gateways without dedicated infrastructure.

Future improvements will address this through cloud deployment and optimized routing.

---
## Author

Cybersecurity student building hands-on security labs to develop practical skills in:

- Network security
- Infrastructure hardening
- Threat detection
- Secure remote access architectures
