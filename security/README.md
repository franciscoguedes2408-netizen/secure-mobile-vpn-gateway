# Security Configuration

This section includes firewall rules, Fail2Ban configuration
and other hardening measures used in the project.
# Security Configuration

This project includes several security controls to reduce the attack surface of the VPN gateway.

## Firewall (UFW)

The firewall is configured using a default deny policy.

Default policies:

deny incoming  
allow outgoing  

Allowed services:

22/tcp – SSH administration  
51820/udp – WireGuard VPN  

This ensures that only essential services are accessible.

## Fail2Ban

Fail2Ban protects the SSH service against brute-force attacks.

Configuration highlights:

maxretry = 3  
findtime = 10m  
bantime = 1h  

If an IP address fails authentication three times within ten minutes,
it is banned for one hour.

## Reduced Host Visibility

ICMP echo responses are restricted to reduce visibility to network scanning tools.
