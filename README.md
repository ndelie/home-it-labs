# Home IT Labs

Hands-on help desk and networking labs built on a MacBook with an Apple chip and a Windows 11 virtual machine in UTM. Each lab records the steps, the results, every problem I hit and how I fixed it.

| Lab | Focus | Key skills |
| --- | --- | --- |
| [Lab 1: Network Troubleshooting and Firewall Security](lab-1-network-troubleshooting/) | Home network mapping, connectivity testing, firewall rules | `ping`, `tracert`, `nslookup`, `ipconfig /release /renew /flushdns`, `arp -a`, Windows Defender Firewall profiles and inbound rules |
| [Lab 2: Windows 11 VM Help Desk Lab](lab-2-windows11-helpdesk-vm/) | Virtual machine build, user accounts, permissions | UTM on Apple Silicon, Windows 11 ARM64 install, local users and groups, password resets with `lusrmgr.msc` and `net user`, NTFS permissions and inheritance, VM backup |

## Lab environment

| Item | Detail |
| --- | --- |
| Host | MacBook Air with Apple chip (ARM64), macOS |
| Hypervisor | UTM, QEMU ARM virtual machine |
| Guest OS | Windows 11 Pro ARM64 |
| VM resources | 8 GB RAM, 4 CPU cores, 64 GB disk |
| Network | Xfinity home network, UTM Shared Network (NAT) for the VM |

## Skills summary

- Built and troubleshot a Windows 11 VM on Apple Silicon, including UEFI boot failures and ISO architecture mismatches
- Created and managed local user accounts, groups and admin rights
- Reset passwords through the GUI and the command line, and enforced password changes at next sign-in
- Applied least-privilege NTFS permissions and diagnosed inherited permission problems
- Diagnosed network problems layer by layer and resolved a simulated DHCP outage
- Read firewall profiles and opened a single protocol through Windows Defender Firewall
- Documented every ticket with symptom, cause and fix
