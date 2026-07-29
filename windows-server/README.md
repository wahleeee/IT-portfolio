# Windows Server Administration Labs

Guided, hands-on labs in a virtualized Windows Server 2022 / Active Directory environment (`globomantics` domain). These reinforce core sysadmin and security skills — directory services, network services, policy enforcement, backup/recovery, and disk encryption — that underpin day-to-day endpoint and infrastructure work.

> **Track note:** These are structured lab courses run in a provided environment, not self-architected homelab builds. They're documented here as a skills/training track to demonstrate breadth across Windows Server administration.

## Labs

| Lab | Focus | Key skills |
|-----|-------|------------|
| [Active Directory Domain Services](#active-directory-domain-services) | Forest & domain setup | AD DS role install, DC promotion, OUs, user management |
| [DNS & DHCP Server Roles](#dns--dhcp-server-roles) | Core network services | Forward lookup zones, A/CNAME records, DHCP scopes & reservations |
| [Group Policy Management](#group-policy-management) | Policy enforcement | GPO creation/linking, drive mapping, RSOP validation |
| [Windows Server Backup](#windows-server-backup) | Data protection | Scheduled/manual backups, remote share target, file recovery |
| [Disk Management & BitLocker](#disk-management--bitlocker) | Storage & encryption | GPT init, NTFS volumes, BitLocker encryption & recovery |

---

## Active Directory Domain Services

Stood up a new AD DS forest by installing the role and promoting the server to a Domain Controller for `corp.globomantics.com`, with DNS and Global Catalog enabled at the Server 2016 functional level. Built a nested OU hierarchy (Staff and Students under Globomantics Users) with accidental-deletion protection, then created and managed user accounts through the Active Directory Administrative Center — setting UPNs, enforcing password-change-at-logon and account expiration, and moving objects between OUs.

**Skills:** AD DS role deployment · Domain Controller promotion · forest/domain functional levels · OU design · user account lifecycle · ADAC

---

## DNS & DHCP Server Roles

Installed the DNS and DHCP roles on Windows Server 2022 and configured core network services. Created a `globomantics.com` forward lookup zone with A and CNAME records, and validated resolution against the local server using PowerShell `Resolve-DnsName -Server 127.0.0.1`. Configured and activated a DHCP scope (`192.168.1.100–200`) with an exclusion range, default gateway, DNS, and parent-domain options, plus a MAC-based reservation for a static device.

**Skills:** DNS zones & records · CNAME aliasing · `Resolve-DnsName` · DHCP scopes · exclusion ranges · address reservations

---

## Group Policy Management

Deployed and validated Group Policy Objects in a `globomantics.co` domain. Created and linked two GPOs to a target OU: one enforcing a standardized user environment (locked desktop personalization plus a persistent G: drive mapping to `\\FS01\FileShare` via Drive Maps preferences), and one restricting access to Registry Editor. Verified enforcement using `gpupdate /force`, `gpresult /r`, and the Resultant Set of Policy (RSOP) tool, confirming policies applied correctly to users in the OU.

**Skills:** GPO creation & linking · Administrative Templates · Group Policy Preferences (drive maps) · `gpupdate` / `gpresult` · RSOP

---

## Windows Server Backup

Installed and configured Windows Server Backup on Server 2022. Tuned backup performance (incremental/delta after an initial full), set up a remote SMB share as the backup destination, and scheduled automated backups targeting specific volumes with credentialed authentication. Performed an on-demand manual backup, then simulated data loss and restored a deleted file end-to-end using the Recovery Wizard.

**Skills:** feature installation · backup scheduling · remote share targets · performance tuning · file & folder recovery

---

## Disk Management & BitLocker

Provisioned a new disk end-to-end: brought it online, initialized it as GPT, and created a 10 GB NTFS volume mounted as D:. Enabled BitLocker on the data drive with a password unlock method, exported the recovery key, and encrypted used space. Validated the full recovery workflow — locking the drive via GUI and PowerShell (`Lock-BitLocker`), unlocking with both password and recovery key, then decrypting to remove protection.

**Skills:** disk initialization (GPT) · NTFS volume creation · BitLocker encryption · recovery key management · `Lock-BitLocker`
