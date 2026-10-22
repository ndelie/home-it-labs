# Lab 2: Windows 11 Virtual Machine on a Mac (Help Desk Lab)

Built a Windows 11 virtual machine on an Apple Silicon Mac with UTM, then performed core help desk tasks: user accounts, password resets (GUI and command line), NTFS folder permissions, and VM backup.

**Dates:** October 14 to 15, 2026
**Time:** about 6.5 hours across two sessions

## Environment

| Item | Detail |
| --- | --- |
| Host | MacBook with Apple chip (ARM64) |
| Hypervisor | UTM, QEMU 10.0 ARM virtual machine |
| Guest OS | Windows 11 Pro ARM64, build 26H2 26300.9457 |
| VM resources | 8 GB RAM, 4 CPU cores, 64 GB disk |
| Accounts | LabAdmin (admin), itsupport (admin), jsmith (standard user) |

## Skills demonstrated

- Virtual machine setup and troubleshooting (UEFI boot, ISO architecture, guest drivers)
- Local user and group management in Settings and lusrmgr.msc
- Password resets with the GUI and with `net user`
- NTFS permissions, inheritance, and least-privilege access
- Testing changes as the end user
- VM backup by cloning

## Part A: Build and install

1. Confirmed the Mac uses an Apple chip (ARM64), then downloaded the Windows 11 Arm64 ISO from Microsoft.
2. Created the VM in UTM: Virtualize > Windows, 8 GB RAM, 4 cores, 64 GB storage.
3. Installed Windows 11 Pro without a product key. Created local admin account LabAdmin.
4. Installed UTM guest tools from the mounted CD drive for display, network, and clipboard drivers.

![Windows desktop as LabAdmin](screenshots/01-desktop-labadmin.jpg)

## Part B: Help desk tasks

| # | Task | How | Result |
| --- | --- | --- | --- |
| 1 | Create standard user | Settings > Accounts > Other users > Add account, no Microsoft account | jsmith created as Local account |
| 2 | Create second admin | Same path, then Change account type > Administrator | itsupport created as Administrator |
| 3 | Reset password (GUI) | `lusrmgr.msc` > Users > jsmith > Set Password, check *User must change password at next logon* | Flag set |
| 4 | Reset password (command) | Admin terminal: `net user jsmith Welcome2026!` then `net user jsmith` | Password reset, account details verified |
| 5 | Test as user | Sign in as jsmith | Windows forced a password change |
| 6 | Folder permissions | `C:\Shared\Finance`: disable inheritance, remove Authenticated Users and Users, grant jsmith Read & execute | Admins and SYSTEM full control, jsmith read only |
| 7 | Test permissions | As jsmith, open and edit budget.txt, then save | Read worked, save denied |
| 8 | Back up VM | UTM > Clone | Win11-Lab 2 created (26.97 GB) |

### Screenshots

![Other users list](screenshots/02-other-users.jpg)
![jsmith properties](screenshots/03-jsmith-properties.jpg)
![net user output](screenshots/04-net-user-output.jpg)
![Password changed](screenshots/05-password-changed.jpg)
![Finance permissions](screenshots/06-finance-permissions.jpg)
![Access denied](screenshots/07-access-denied.jpg)
![UTM clone](screenshots/08-utm-clone.jpg)

## Full walkthrough

Every screen in order, including the problems. Files starting with a are Part A (October 14), b are Part B (October 15).

<details>
<summary>Show all 43 screenshots</summary>

**A01. Problem uefi boot manager**

![Problem uefi boot manager](screenshots/walkthrough/a01-problem-uefi-boot-manager.jpg)

**A02. Problem boot manager retry**

![Problem boot manager retry](screenshots/walkthrough/a02-problem-boot-manager-retry.jpg)

**A03. Fix deleted vm start over**

![Fix deleted vm start over](screenshots/walkthrough/a03-fix-deleted-vm-start-over.jpg)

**A04. Download windows11 arm64 iso**

![Download windows11 arm64 iso](screenshots/walkthrough/a04-download-windows11-arm64-iso.jpg)

**A05. Vm hardware 8gb 4cores**

![Vm hardware 8gb 4cores](screenshots/walkthrough/a05-vm-hardware-8gb-4cores.jpg)

**A06. Windows setup select disk**

![Windows setup select disk](screenshots/walkthrough/a06-windows-setup-select-disk.jpg)

**A07. Problem booted from install media**

![Problem booted from install media](screenshots/walkthrough/a07-problem-booted-from-install-media.jpg)

**A08. Fix eject iso**

![Fix eject iso](screenshots/walkthrough/a08-fix-eject-iso.jpg)

**A09. Oobe keyboard layout**

![Oobe keyboard layout](screenshots/walkthrough/a09-oobe-keyboard-layout.jpg)

**A10. Create local account**

![Create local account](screenshots/walkthrough/a10-create-local-account.jpg)

**A11. Desktop labadmin**

![Desktop labadmin](screenshots/walkthrough/a11-desktop-labadmin.jpg)

**A12. File explorer**

![File explorer](screenshots/walkthrough/a12-file-explorer.jpg)

**A13. Utm guest tools cd**

![Utm guest tools cd](screenshots/walkthrough/a13-utm-guest-tools-cd.jpg)

**A14. Guest tools installing**

![Guest tools installing](screenshots/walkthrough/a14-guest-tools-installing.jpg)

**B01. Jsmith created**

![Jsmith created](screenshots/walkthrough/b01-jsmith-created.jpg)

**B02. Itsupport administrator**

![Itsupport administrator](screenshots/walkthrough/b02-itsupport-administrator.jpg)

**B03. Lusrmgr users**

![Lusrmgr users](screenshots/walkthrough/b03-lusrmgr-users.jpg)

**B04. Lusrmgr groups**

![Lusrmgr groups](screenshots/walkthrough/b04-lusrmgr-groups.jpg)

**B05. Problem wrong account properties**

![Problem wrong account properties](screenshots/walkthrough/b05-problem-wrong-account-properties.jpg)

**B06. Problem mmc close dialogs error**

![Problem mmc close dialogs error](screenshots/walkthrough/b06-problem-mmc-close-dialogs-error.jpg)

**B07. Jsmith must change password**

![Jsmith must change password](screenshots/walkthrough/b07-jsmith-must-change-password.jpg)

**B08. Problem delete prompt clicked no**

![Problem delete prompt clicked no](screenshots/walkthrough/b08-problem-delete-prompt-clicked-no.jpg)

**B09. Start menu search**

![Start menu search](screenshots/walkthrough/b09-start-menu-search.jpg)

**B10. Admin powershell**

![Admin powershell](screenshots/walkthrough/b10-admin-powershell.jpg)

**B11. Problem missing net user**

![Problem missing net user](screenshots/walkthrough/b11-problem-missing-net-user.jpg)

**B12. Problem stray colon**

![Problem stray colon](screenshots/walkthrough/b12-problem-stray-colon.jpg)

**B13. Correct net user command**

![Correct net user command](screenshots/walkthrough/b13-correct-net-user-command.jpg)

**B14. Net user jsmith output**

![Net user jsmith output](screenshots/walkthrough/b14-net-user-jsmith-output.jpg)

**B15. Problem missing space syntax**

![Problem missing space syntax](screenshots/walkthrough/b15-problem-missing-space-syntax.jpg)

**B16. Fix logonpasswordchg**

![Fix logonpasswordchg](screenshots/walkthrough/b16-fix-logonpasswordchg.jpg)

**B17. Jsmith password changed**

![Jsmith password changed](screenshots/walkthrough/b17-jsmith-password-changed.jpg)

**B18. Jsmith first signin**

![Jsmith first signin](screenshots/walkthrough/b18-jsmith-first-signin.jpg)

**B19. Finance security inherited**

![Finance security inherited](screenshots/walkthrough/b19-finance-security-inherited.jpg)

**B20. Advanced security inherited from c**

![Advanced security inherited from c](screenshots/walkthrough/b20-advanced-security-inherited-from-c.jpg)

**B21. Inheritance disabled**

![Inheritance disabled](screenshots/walkthrough/b21-inheritance-disabled.jpg)

**B22. Broad groups removed**

![Broad groups removed](screenshots/walkthrough/b22-broad-groups-removed.jpg)

**B23. Jsmith read execute added**

![Jsmith read execute added](screenshots/walkthrough/b23-jsmith-read-execute-added.jpg)

**B24. Jsmith read only permissions**

![Jsmith read only permissions](screenshots/walkthrough/b24-jsmith-read-only-permissions.jpg)

**B25. Jsmith save as**

![Jsmith save as](screenshots/walkthrough/b25-jsmith-save-as.jpg)

**B26. Jsmith save denied**

![Jsmith save denied](screenshots/walkthrough/b26-jsmith-save-denied.jpg)

**B27. Utm vm stopped**

![Utm vm stopped](screenshots/walkthrough/b27-utm-vm-stopped.jpg)

**B28. Utm clone confirm**

![Utm clone confirm](screenshots/walkthrough/b28-utm-clone-confirm.jpg)

**B29. Utm clone created**

![Utm clone created](screenshots/walkthrough/b29-utm-clone-created.jpg)

</details>

## Problems and fixes

| Symptom | Cause | Fix |
| --- | --- | --- |
| VM booted to UEFI Boot Manager | No Windows installer attached, only the guest tools ISO | Deleted VM, rebuilt with the correct ISO |
| Installer would not boot | Mac needs the ARM64 ISO, not x64 | Downloaded Windows 11 Arm64 ISO |
| Setup said "booted from installation media" after restart | VM booted from the ISO again | Ejected the ISO in UTM, clicked Yes |
| Guest tools finished without restarting | No reboot prompt | Restarted from Start > Power |
| Delete prompt appeared for jsmith | Red X in lusrmgr toolbar means Delete | Clicked No, closed with the window X |
| `net user` showed syntax help | Missing space: `jsmith/logonpasswordchg:yes` | `net user jsmith /logonpasswordchg:yes` |
| Must-change flag cleared after Step 4 | A `net user` password reset clears the flag | Re-enabled with `/logonpasswordchg:yes` |
| Read-only grant would not restrict jsmith | Authenticated Users had Modify, inherited from C:\ | Disabled inheritance, removed broad groups |
| Save succeeded during the test | Test ran as LabAdmin (admin) | Repeated the test as jsmith |

## Lessons learned

- Match the ISO to the CPU. Apple Silicon needs Windows ARM64.
- Disable accounts before deleting them. Each account has a unique SID, and a recreated account does not regain old access.
- Re-check flags after a command-line password reset.
- Check inheritance first when a permission change seems to do nothing.
- Test as the restricted user. An admin passes every test and proves nothing.
