[GitHub_01_ActiveDirectory_README.md](https://github.com/user-attachments/files/27048050/GitHub_01_ActiveDirectory_README.md)# 🏢 Active Directory Infrastructure Lab

![Windows Server](https://img.shields.io/badge/Windows_Server-2019-0078D6?style=flat-square&logo=windows&logoColor=white)
![Active Directory](https://img.shields.io/badge/Active_Directory-AD_DS-0078D6?style=flat-square&logo=microsoft&logoColor=white)
![VirtualBox](https://img.shields.io/badge/Virtualisation-VirtualBox-183A61?style=flat-square&logo=virtualbox&logoColor=white)
![Status](https://img.shields.io/badge/Status-Running-brightgreen?style=flat-square)

A fully simulated enterprise domain environment built from scratch in a personal home lab. This project replicates the core identity and policy infrastructure found in mid-size organisations — covering authentication, group policy enforcement, and network services.

---

## 🎯 Objective

To build and administer a production-equivalent Windows Server environment that demonstrates real-world Active Directory skills — the kind required for IT Support, Junior SysAdmin, and Network Administrator roles.

---

## 🛠️ Environment

| Component | Details |
|---|---|
| Hypervisor | Oracle VirtualBox |
| Domain Controller OS | Windows Server 2019 |
| Client OS | Windows 10 Pro |
| Network Mode | Internal Network + NAT |
| Domain Name | corp.mortsilab.local |

---

## ✅ What Was Built

### 1. Active Directory Domain Services (AD DS)
- Promoted a Windows Server 2019 VM to Domain Controller
- Configured a new AD forest: `corp.mortsilab.local`
- Joined Windows 10 client machines to the domain successfully

### 2. Organisational Unit (OU) Structure
Designed a clean OU hierarchy mirroring a real company layout:
```
corp.mortsilab.local
├── IT Department
│   ├── Admins
│   └── Support
├── Finance
├── HR
└── Workstations
    ├── Laptops
    └── Desktops
```

### 3. User & Group Management
- Created 20+ test user accounts with standardised naming conventions
- Assigned users to appropriate security groups
- Configured account policies: password expiry, lockout thresholds, complexity requirements

### 4. Group Policy Objects (GPOs)
Implemented and tested the following GPOs:

| GPO | Scope | Purpose |
|---|---|---|
| Password Policy | Domain | Min 10 chars, complexity, 90-day expiry |
| Desktop Lockdown | Workstations OU | Restrict Control Panel, disable USB |
| Drive Mapping | IT Department | Auto-map shared network drives on login |
| Software Restriction | Finance OU | Block execution of unauthorised .exe files |
| Login Banner | Domain | Display acceptable-use notice at logon |

### 5. DNS Configuration
- Configured forward lookup zones for `corp.mortsilab.local`
- Created A records and verified name resolution across domain-joined machines
- Tested reverse lookup zone for PTR records

### 6. DHCP Configuration
- Set up DHCP scope: `192.168.10.0/24`
- Configured IP exclusions for servers and printers
- Tested dynamic IP assignment on client machines
- Configured DHCP reservations for key devices

---

## 🔍 Key Troubleshooting Scenarios Practised

- Domain join failures due to DNS misconfiguration → fixed by pointing client DNS to DC IP
- GPO not applying → resolved using `gpresult /r` and `gpupdate /force`
- DHCP scope exhaustion simulation → resolved by adjusting lease duration and scope range
- User account lockouts → investigated via Event Viewer (Event ID 4740)

---

## 📸 Screenshots

> _Screenshots of the lab environment will be added here — OU structure, GPO editor, DHCP console, and ADUC._

---

## 📚 Skills Demonstrated

`Active Directory` `AD DS` `Group Policy` `DNS` `DHCP` `Windows Server 2019` `VirtualBox` `User Management` `OU Design` `Domain Administration` `Event Viewer` `PowerShell`

---

## 🔗 Related Projects

- [Network Engineering & CCNA Lab](../02-ccna-network-lab)
- [Linux Server Administration Lab](../03-linux-server-lab)
- [Enterprise Virtual Lab Environment](../04-virtualisation-lab)
