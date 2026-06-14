# DNS & DHCP

## DNS Server

- **Role**: Active Directory Integrated DNS
- **Server**: Homelab-DC (Windows Server 2022)
- **Zone**: homelab.local (Forward Lookup Zone)
- **PTR Records**: Reverse Lookup Zone configured

## DHCP Server

- **Role**: DHCP Server on Domain Controller
- **Scope**: Homelab_LAN
- **Range**: X.X.X.150 - X.X.X.200
- **Subnet Mask**: 255.255.255.0
- **DNS Server**: Distributed automatically to clients
- **Gateway**: Distributed automatically to clients
- **Lease Duration**: 8 days

## Notes

- DNS integrated with Active Directory — records registered automatically when machines join domain
- DHCP authorized in Active Directory
- Static IPs reserved outside DHCP scope for servers and infrastructure devices
