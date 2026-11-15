# Lab Progress — Windows Server Active Directory

## Project objective

Build and document a small, isolated Windows Server Active Directory lab to practise server administration, AD DS, DNS, domain-controller configuration, and troubleshooting.

This is a learning lab, not a production deployment.

## Hardware and environment

| Component | Current setup |
|---|---|
| Platform | Physical desktop computer |
| Operating system | Windows Server 2022 |
| CPU | AMD Phenom II X4 965, 4 cores / 4 threads |
| Memory | 4 GB DDR3 |
| Firmware | Legacy BIOS |
| Network adapter | Realtek PCIe GbE Family Controller |
| Server hostname | `YG-DC01` |
| Planned AD DNS domain | `yglab.test` |
| Planned NetBIOS domain | `YGLAB` |

The lab is being built on older hardware with limited memory. Performance and compatibility constraints are part of the troubleshooting exercise.

## Work completed

- [x] Prepared the external hard drive as bootable installation media using Ventoy.
- [x] Installed Windows Server 2022.
- [x] Completed initial server setup and signed in.
- [x] Renamed the server to `YG-DC01`.
- [x] Installed the Active Directory Domain Services (AD DS) role.
- [x] Started the AD DS promotion wizard.
- [x] Selected **Add a new forest** with root domain `yglab.test`.
- [x] Kept DNS Server and Global Catalog selected.
- [x] Set the planned NetBIOS name to `YGLAB`.
- [x] Kept the default database, log, and SYSVOL paths.

## Current status

**Status: In progress**

The domain-controller promotion has **not** completed.

The prerequisite check stopped with this error:

> The TCP/IP networking protocol must be properly configured.

The server was intended to run as an isolated offline lab using a static IPv4 configuration. The Ethernet adapter showed **Media disconnected** when the cable was unplugged. A later diagnostic showed that the adapter had obtained DHCP settings from the university network. That campus connection is not part of the intended lab topology and its network details are deliberately not published here.

## Next steps

1. Disconnect the server from the university network.
2. Inspect and verify the Ethernet adapter's IPv4 configuration while offline.
3. Confirm that Windows recognises the adapter configuration and that the server uses its own address for DNS.
4. Re-run the AD DS prerequisite check.
5. Complete promotion only after the TCP/IP prerequisite passes.
6. Verify the domain, DNS records, and domain-controller health.
7. Document each completed task with genuine screenshots or sanitised command output.

## Planned validation

After successful promotion, collect and explain the output of:

```powershell
Get-ADDomain
Get-ADForest
Get-ADDomainController -Filter *
Get-DnsServerZone
dcdiag
```

Also verify DNS service records and FSMO role ownership. These checks are planned; their results have not yet been collected.

## Security and evidence rules

- Keep the domain controller off the university network while the lab is isolated.
- Do not publish passwords, DSRM credentials, recovery keys, tokens, or private information.
- Do not publish campus network addresses, DNS servers, or other internal network details.
- Use screenshots and command output from the actual lab only.
- Mark an exercise complete only after it has been performed and verified.
