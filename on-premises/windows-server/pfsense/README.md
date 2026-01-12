# 🧱 Documentation of the pfSense Firewall environment  
**Project:** On-Premises Infrastructure - Azure Integration  
**Firewall server:** pfSense 2.7.x  
**Author:** Miquéias Alves Ferreira  
**Local:** Network Ferreira.local  

---

## 🔹 Step 1 - Initial Configuration and Administrative Access

**Purpose:** Prepare pfSense to act as the main firewall and gateway for the local network.

### 1.1 Administrative Access
- Access address: 'https://192.168.10. 1'
- Configured interface: **LAN**
- Default password changed to secure credentials.
- Setting of **Time Zone:** ‘Europe/Lisbon’
- Configuration of **Hostname:** 'firewall'
- Domain configured: 'ferreira.local'

---

## 🔹 Step 2 - Configuration of Interfaces and Internal Network

### 2.1 LAN interface
- IP LAN: '192.168.10.1/24'
- Gateway: automatic
- DHCP disabled on pfSense (the service is provided by Windows Server)

### 2.2 WAN Interface
- IP WAN: assigned via DHCP (external provider)
- NAT configured to allow outgoing hosts from the internal network to the Internet.

---

## 🔹 Step 3 - Firewall (LAN) Rules

### 3.1 Applied Policies

| No | Action | Origin | Destination | Port | Description |
|----|-------|---------|----------|--------|------------|
| 1 | ✅ Allow | LAN Net | This Firewall | 53 (DNS) | Allow DNS only for Windows Server |
| 2 | ✅ Allow | LAN Net | This Firewall | 67-68 (DHCP) | Allow DHCP between LAN and pfSense |
| 3 | ✅ Allow | LAN Net | any | 80, 443 | Allow web browsing (HTTP/HTTPS) |
| 4 | ⛔ Block | LAN Net | any | any | Block all the rest (last rule) |

> **Note:** The rules are processed from top to bottom.  
> The **final block** rule should always remain **at the end of the list**, ensuring that only explicitly allowed traffic is released.

---

## 🔹 Step 4 - Advanced Security Configuration

### 4.1 IDS/IPS - Meerkat
- Installed the extension **Suricata** via Package Manager.
- Monitored interface: **LAN**
- Mode: **Inline IPS**
- Rules enabled: 'ET Open Rules'
- Settings:
  - Automatic blocking of malicious IPs.
  - Active logging in `/var/log/suricata/.
  - Automatic update of the rules every 12h.

### 4.2 GeoIP Blocking (optional)
- Blocked countries: Russia, China, North Korea.
- Traffic from trusted regions only allowed.

---

## 🔹 Step 5 - Preparing for Azure Integration

### 5.1 VPN Planning
- Expected connection type: **IPsec Site-to-Site**
- Status: waiting for configuration on the Azure side.
- No temporary virtual interface created (will be done after Azure endpoint is configured).
- IPsec Phase 1 and Phase 2 will be deployed later according to Azure virtual gateway parameters.

---

## 🔹 Step 6 - Testing and Validation

### 6.1 Connectivity
- Ping pfSense Windows Server: **OK**
- Windows Server pfSense ping: **OK**
- Internal clients (VMs) with internet access: **OK**

### 6.2 Block Test
- Attempted access to IP not allowed: registered block (packet discarded).

---

## 🔹 Final Policy Structure

``plaintext
[LAN Rules - Top to Bottom ]
1. Allow DNS (53/TCP-UDP)   Windows Server
2. Allow DHCP (67-68/UDP)
3. Allow HTTP/HTTPS any
4. Block All (default deny)
