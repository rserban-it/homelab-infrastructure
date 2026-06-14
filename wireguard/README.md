# WireGuard VPN

## Overview

WireGuard VPN server deployed on Ubuntu Server for secure remote access to the homelab network.

## Configuration

- **Server**: Ubuntu Server VM on Proxmox
- **Protocol**: WireGuard (UDP)
- **NAT**: Configured for traffic routing through VPN tunnel
- **DNS over VPN**: Pi-hole DNS active when connected via VPN

## What Works

- Phone connects remotely through WireGuard tunnel
- Pi-hole DNS filtering active over VPN connection
- Full access to homelab network resources remotely

## Key Commands

```bash
# Check WireGuard status
sudo wg show

# Start/stop WireGuard
sudo systemctl start wg-quick@wg0
sudo systemctl stop wg-quick@wg0

# Enable on boot
sudo systemctl enable wg-quick@wg0
```
