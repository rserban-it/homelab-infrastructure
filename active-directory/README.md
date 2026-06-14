# Active Directory

## Domain Information

- **Domain**: homelab.local
- **NetBIOS**: HOMELAB
- **Domain Controller**: Homelab-DC
- **Functional Level**: Windows Server 2016

## Organizational Units

- Employees — domain users
- Servers — server objects
- Service Accounts — service and application accounts

## Users

Domain users created and managed via Active Directory Users and Computers.

## Security Groups

- **IT_staff** (Global Security) — contains all domain users

## Group Policy

- **Desktop_Policy** — linked to Employees OU

## Key Commands

```powershell
# Force Group Policy update
gpupdate /force

# Query FSMO roles
netdom query fsmo

# Check domain controller
nltest /dsgetdc:homelab.local
```
