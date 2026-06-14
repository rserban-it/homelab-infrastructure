# Lessons Learned

Real troubleshooting issues encountered during homelab build and how they were resolved.

## Windows 11 Domain Join — IPv6 Interference

**Problem**: Windows 11 client could not join Active Directory domain. Error: "The operation is only allowed for the Primary Domain Controller" and "homelab.local could not be contacted".

**Troubleshooting steps taken**:
- Verified DNS resolution (working with explicit server IP)
- Verified network connectivity — ping, ports 445, 88, 53 all open
- Checked FSMO roles on DC — all correct
- Time sync between client and DC — corrected
- Disabled Windows Firewall on both machines
- Added manual DNS suffix
- Added hosts file entries

**Root cause**: IPv6 was interfering with domain controller discovery on Windows 11.

**Solution**:
```powershell
Disable-NetAdapterBinding -Name "Ethernet" -ComponentID ms_tcpip6
```

**Lesson**: Always disable IPv6 on Windows clients before domain join in lab environments. IPv6 can interfere with Kerberos and DC discovery even when IPv4 connectivity is fully functional.

---

## DNS Resolution — Windows Server Not Responding on IPv6

**Problem**: DNS server not responding to client queries despite port 53 being open.

**Root cause**: DNS service was listening on IPv6 address instead of IPv4.

**Solution**: DNS Manager → Server Properties → Interfaces → removed IPv6 address, kept only IPv4. Restarted DNS service.

---

## Linux Domain Join — DNS Configuration

**Problem**: Ubuntu could not discover homelab.local domain after installing realmd.

**Root cause**: Pi-hole was set as DNS server. Pi-hole resolves internet DNS but has no knowledge of internal AD domain records.

**Solution**: Changed DNS on Ubuntu to point to Windows Server DC instead of Pi-hole. Windows Server DNS has all AD records registered automatically.

**Long term fix planned**: Configure Pi-hole to forward homelab.local queries to Windows Server DNS.
