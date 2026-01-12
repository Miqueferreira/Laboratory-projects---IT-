# 🖥️ Windows Server 2022 Environment Documentation  
**Project:** On-Premises Infrastructure - Ferreira.local  
**Server:** SVR01  
**Author:** Miquéias Alves Ferreira  
**Local:** Network Ferreira.local  

---

## 🔹 Step 1 - Initial Server Configuration

### 1.1 Identification and Network
- **Hostname:** ‘SVR01’
- **Domain:** “Ferreira.local”
- **IP address:** ‘192.168.10.10’
- **Mask:** ‘255.255.255.0’
- **Gateway:** ‘192.168.10.1’ (pfSense)
- **Preferred DNS:** ‘127.0.0.1’
- **Alternate DNS:** ‘192.168.10.1’

---

## 🔹 Step 2 - Active Directory and DNS

### 2.1 Promotion to Domain Controller
- Installed the **Active Directory Domain Services (AD DS)** service.  
- Created the domain: 'Ferreira.local'.  
- DNS integrated to the configured AD.  
- DNS forwarder pointing to pfSense ('192.168.10.1').  

### 2.2 Organizational Unit Structure (OUs)

`
Ferreira.local
Departments
Financial
IT
Accounting
Administrative
Legal
RH
SAC
Computers
Users
`

---

## 🔹 Step 3 - DHCP Server

### 3.1 Installation and Configuration
- Service **DHCP Server** installed and authorized.  
- **Scope:**  
  - Range: ‘192.168.10.100’   ‘192.168.10.200’  
  - Gateway: '192.168.10.1'  
  - DNS: '192.168.10.10'  
  - Lease: '8 hours'  
- Optional reservations for critical equipment.  

### 3.2 Exclusions
- Out of scope IPs used as fixed:  
  - '192.168.10.1‘pfSense  
  - ‘192.168.10.10‘   SVR01  

---

## 🔹 Step 4 - File Sharing (File Server)

### 4.1 Final Structure of Folders and Permissions

**Base path:** ‘D: Shares’

`
D: Shares
Public
(Permission: All - Read/Write)
Company
Financial
Accounting
Administrative
Legal
RH
SAC
IT
IT
`

**Default permissions applied:**

| Folder | NTFS permissions | Sharing |
|------|------------------|------------------|
| Public | All: Read/Write | All: Read/Write |
| Financial | Financial Group: Modify | Financial: Modify |
| Accounting | Group Accounting: Modify | Accounting: Modify |
| Administrative | Administrative Group: Modify | Administrative: Modify |
| Legal | Legal Group: Modify | Legal: Modify |
| HR | HR Group: Modify | HR: Modify |
| SAC | Group SAC: Modify | SAC: Modify |
| IT | Group IT: Total Control | IT: Total Control |

### 4.2 Names of Created Shares

`
SVR01 Publico
SVR01 Financial
SVR01 Accounting
SVR01 Administrative
SVR01 Juridico
SVR01 RH
SVR01 SAC
SVR01 IT
`

---

## 🔹 Step 5 - Essential GPOs

### GPO 1 - Map Network Units

**Local:** ‘User Configuration > Preferences > Windows Settings > Drive Maps’  

**Configured mappings:**

`
Publico SVR01 Publico Letra P:
Financial SVR01 Financial Letra F:
Accounting SVR01 Accounting Letter C:
Administrative SVR01 Administrativo Letra A:
Juridico SVR01 Juridico Letra J:
RH SVR01 RH Letra R:
SAC SVR01 SAC Letter S:
IT SVR01 IT Letra I:
`

Applied to the respective security groups.

---

## 🔹 Step 6 - Backups (Overview)

- Backup configured using **Windows Server Backup**.  
- Recommended destination: external disk or NAS.  
- Items: System State, AD, DNS, DHCP, Shares.  
- Suggested frequency: daily.  

---

## ✅ Production-ready environment  
Infrastructure mounted with AD, DNS, DHCP, File Server and main GPOs configured.
