# Cloud Environment – Implemented Azure Lab

This directory documents the **Azure cloud environment implemented in this lab**, focusing on real-world configurations executed to integrate an on-premises Active Directory environment with Microsoft Azure.

The implementation follows enterprise best practices for **identity, networking, security, and resilience**, using Microsoft Entra ID as the central identity provider.

---

## Scope of the Implemented Cloud Lab

The following components were **designed, deployed, and validated** as part of this lab:

---

## 1️⃣ Azure Subscription & Resource Organization

- Single Azure subscription used to host all cloud resources
- Logical resource separation applied using:
  - Resource Groups per function (identity, networking, security)
- Naming conventions aligned with enterprise standards
- Lab structured to simulate a production-ready environment

---

## 2️⃣ Networking (VNets, Subnets & NSGs)

- Azure Virtual Network deployed to support identity and hybrid services
- Subnets segmented by role (identity services, future workloads)
- Network Security Groups (NSGs) applied at subnet level with:
  - Explicit inbound allow rules for identity-related traffic
  - Default deny-all policy for unauthorized access
- Network rules designed to support:
  - On-premises connectivity
  - Active Directory synchronization
  - Secure DNS and authentication traffic

---

## 3️⃣ Microsoft Entra ID (Azure Active Directory)

- Microsoft Entra ID configured as the **cloud identity authority**
- Hybrid identity model implemented
- Integration with on-premises Active Directory using Azure AD Connect
- Cloud identities synchronized and validated

---

## 4️⃣ Identity Synchronization (Azure AD Connect)

- Azure AD Connect deployed and configured
- Password Hash Synchronization (PHS) enabled
- On-premises users synchronized to Microsoft Entra ID
- Identity flow validated from on-premises AD to cloud

---

## 5️⃣ Identity Security (MFA, Conditional Access & Identity Protection)

- Multi-Factor Authentication (MFA) enforced using Conditional Access
- Security policies implemented based on:
  - User risk
  - Sign-in risk
- Microsoft Entra Identity Protection configured to:
  - Detect risky sign-ins
  - Detect compromised identities
- Conditional Access policies applied to protect privileged and standard users

---

## 6️⃣ Backup, Security & Disaster Recovery Considerations

- Identity-focused security posture implemented
- Protection of authentication and access layers prioritized
- Foundation established for:
  - Business continuity
  - Disaster recovery scenarios
  - Future workload expansion

---

## Lab Objectives

The primary objective of this lab was to **simulate a real enterprise hybrid identity environment**, focusing on:

- Secure integration between on-premises Active Directory and Azure
- Strong identity protection using native Microsoft security services
- Network segmentation and access control
- Cloud-ready architecture aligned with best practices

---

## Notes

This repository documents **an executed lab**, not a theoretical design.  
All configurations were implemented, tested, and validated as part of hands-on practice.
