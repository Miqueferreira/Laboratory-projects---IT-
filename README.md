# 🧱 Hybrid Infrastructure Lab (On-Premises + Azure Design)

## 👤 Author

**Miquéias Alves Ferreira**
Infrastructure | Cloud | Security

---

## 📘 Project Overview

This repository documents a **secure on‑premises infrastructure** integrated with a **cloud-ready design for Microsoft Azure**.

The project was built as a **hands-on lab** focused on:

* Enterprise networking
* Identity management
* Security best practices
* Hybrid cloud preparation

> ⚠️ **Important note**:
> The **on‑premises environment is fully implemented and operational**.
> The **Azure environment is documented as DESIGN / PLANNED**, due to subscription limitations.

---

## 🎯 Project Goals

* Build a secure corporate on‑premises environment
* Implement firewall hardening and IDS/IPS
* Deploy Active Directory, DNS, DHCP and File Services
* Prepare the environment for hybrid integration with Azure
* Design identity synchronization with Microsoft Entra ID
* Design backup and disaster recovery strategy using Azure

---

## 🧱 Implemented Environment (On‑Premises)

### 🔐 Security Layer

* **pfSense Firewall**

  * Stateful firewall rules (default deny)
  * IDS/IPS with **Suricata**
  * DNS and IP blocking with **pfBlockerNG**
  * Secure administrative access (LAN only)

### 🖥️ Server Layer

* **Windows Server 2022 (SVR01)**

  * Active Directory Domain Services (AD DS)
  * DNS Server
  * DHCP Server
  * File Server with role‑based access
  * Group Policy Objects (GPOs)

### 🌐 Network

* Internal network: `192.168.10.0/24`
* Gateway: pfSense (`192.168.10.1`)
* Domain Controller: `192.168.10.10`

---

## ☁️ Cloud Environment (Azure – Design Only)

The Azure environment is **fully designed but not deployed**.

### Planned Components

* Azure Virtual Network (VNet)
* Subnets and NSGs
* Site‑to‑Site VPN (IPsec)
* Microsoft Entra ID (Azure AD)
* Azure AD Connect
* MFA enforcement
* Azure Backup
* Disaster Recovery strategy

All cloud components are documented as **Ready for Implementation**.

---

## 📁 Repository Structure

```text
hybrid-infrastructure-lab/
│
├── README.md
│
├── on-premises/
│   ├── pfsense/
│   │   └── README.md
│   ├── windows-server/
│   │   └── README.md
│
├── cloud-design/
│   ├── azure-architecture.md
│   ├── identity-integration.md
│   ├── backup-dr-plan.md
│   └── security-design.md
│
├── diagrams/
│   └── hybrid-architecture.drawio
│
└── notes/
    └── lessons-learned.md
```

---

## 🔐 Identity Strategy (Planned)

* Azure AD Connect
* Authentication method: **Password Hash Synchronization (PHS)**
* MFA enforcement via Microsoft Entra ID
* OU filtering and group‑based access control

---

## 💾 Backup & Disaster Recovery (Planned)

* Azure Backup for Windows Server
* Recovery Services Vault
* Daily backups
* File‑level and system‑state recovery

---

## 📊 Status Summary

| Component                  | Status        |
| -------------------------- | ------------- |
| pfSense Firewall           | ✅ Implemented |
| Windows Server AD/DNS/DHCP | ✅ Implemented |
| File Server & GPOs         | ✅ Implemented |
| Azure Network              | 🟡 Designed   |
| Azure Identity             | 🟡 Designed   |
| Azure Backup / DR          | 🟡 Designed   |

---

## 🚀 Next Steps

* Add detailed Azure architecture diagrams
* Expand identity federation documentation
* Simulate cloud integration scenarios

---

## 📝 License

This project is licensed under the **MIT License** and can be reused for educational and professional purposes.

---

> 💡 This project reflects real‑world enterprise practices and is suitable for portfolio presentation, certification preparation (AZ‑104 / SC‑300) and technical interviews.

