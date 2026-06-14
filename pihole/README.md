# Pi-hole DNS Filtering

## Overview

Pi-hole deployed as network-wide DNS filtering solution on Ubuntu Server VM.

## Configuration

- **Server**: Ubuntu Server VM on Proxmox
- **Domains Blocked**: 83,000+
- **Scope**: Entire home network (configured as DNS on router)
- **DNS over VPN**: Active when connected via WireGuard

## Integration

- Router configured to use Pi-hole as primary DNS
- WireGuard VPN clients use Pi-hole DNS through tunnel
- Windows Server DNS forwards external queries (internet resolution)

## Key Stats

- 83,600+ domains blocked
- Network-wide ad and tracker blocking
- Custom DNS entries for homelab services
