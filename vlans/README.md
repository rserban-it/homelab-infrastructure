# VLAN Segmentation

## Overview

Network segmentation implemented using 802.1Q VLANs on managed switch.

## Hardware

- **Switch**: TP-Link TL-SG105E (5-port managed switch)
- **Configuration**: 802.1Q VLAN tagging

## VLAN Design

| VLAN ID | Name | Purpose |
|---|---|---|
| 10 | Management | Infrastructure management traffic |
| 20 | Lab | Lab and testing environment |

## Implementation

- VLANs configured via TP-Link Easy Smart Configuration Utility
- Proxmox VMs assigned to VLANs via VLAN tag on network interface
- Inter-VLAN routing planned via pfSense (upcoming)

## Notes

- ISP router does not support inter-VLAN routing
- pfSense VM planned as next step for proper inter-VLAN routing and firewall rules
