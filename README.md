# homelab-infrastructure
Personal homelab build on Proxmox VE - Windows Server, Active Directory, Linux, WireGuard VPN, VLANs, Pi-hole
# Homelab Infrastructure

Personal homelab built from scratch to develop and demonstrate practical skills in system administration, networking, and virtualization.

## Hardware

- **Device**: GMKtec G3S Mini PC
- **CPU**: Intel N95 (4 cores)
- **RAM**: 16GB
- **Storage**: 512GB SSD
- **Switch**: TP-Link TL-SG105E (managed, 802.1Q VLAN support)

## Stack

| Technology | Role |
|---|---|
| Proxmox VE 9.2 | Hypervisor / Virtualization platform |
| Windows Server 2022 | Domain Controller, DNS, DHCP |
| Active Directory DS | User, group and policy management |
| Ubuntu Server 24.04 | Linux domain member, Pi-hole, WireGuard |
| Pi-hole | DNS filtering (83,000+ domains blocked) |
| WireGuard | VPN server with Pi-hole DNS over tunnel |
| 802.1Q VLANs | Network segmentation (Management / Lab) |

## What's Built

- Proxmox VE hypervisor with multiple VMs
- Windows Server 2022 Domain Controller (homelab.local)
- Active Directory with Organizational Units, users, security groups and Group Policies
- DHCP server with configured scope
- Ubuntu Server joined to Active Directory domain via realmd and SSSD
- Windows 11 Enterprise client joined to domain
- WireGuard VPN with NAT and remote access
- Pi-hole DNS filtering integrated across entire home network
- 802.1Q VLAN segmentation on managed switch
  
  ## Network Diagram

![Network Diagram](architecture/network-diagram.svg)


## Status

🟢 Active — ongoing development

## Documentation

Detailed documentation for each component available in the folders above.

## Screenshots

### Proxmox VE Dashboard
![Proxmox Dashboard](architecture/proxmox-dashboard.jpg)

### Pi-hole DNS Filtering
![Pi-hole Dashboard](pihole/pihole-dashboard.png)

## Skills Demonstrated

- Active Directory Administration (Users, Groups, OUs, GPO)
- DNS Management (AD-integrated zones, forwarders)
- DHCP Scope Configuration and Management
- Linux System Administration (Ubuntu Server)
- Identity Management (Linux domain join via realmd/SSSD)
- Group Policy Management and Deployment
- VPN Technologies (WireGuard with NAT)
- Network Segmentation (802.1Q VLANs)
- Virtualization (Proxmox VE, VM lifecycle management)
- Infrastructure Troubleshooting and Documentation

## Troubleshooting Examples

**Windows 11 domain join failed — IPv6 interference**
Symptom: "homelab.local could not be contacted" despite full network connectivity.
Root cause: IPv6 was interfering with Kerberos and DC discovery.
Fix: `Disable-NetAdapterBinding -Name "Ethernet" -ComponentID ms_tcpip6`

**DNS not resolving internal domain on Linux**
Symptom: Ubuntu could not discover homelab.local via Pi-hole DNS.
Root cause: Pi-hole has no knowledge of internal AD records — only Windows Server DNS does.
Fix: Changed DNS on Ubuntu to point directly to Windows Server DC.

## Roadmap

- [ ] Grafana + Prometheus monitoring
- [ ] pfSense VM for inter-VLAN routing and firewall rules
- [ ] Pi-hole DNS forwarding for homelab.local
- [ ] File Server with NTFS permissions and mapped drives via GPO
- [ ] Azure integration (AZ-900 → AZ-104)
- [ ] Backup strategy for AD and VMs
