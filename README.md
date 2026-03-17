<div align="center">

<img src="https://img.shields.io/badge/FortiGate-NGFW-EE3124?style=for-the-badge&logo=fortinet&logoColor=white"/>
<img src="https://img.shields.io/badge/FortiOS-VM-EE3124?style=for-the-badge&logo=fortinet&logoColor=white"/>
<img src="https://img.shields.io/badge/VMware-Workstation-607078?style=for-the-badge&logo=vmware&logoColor=white"/>
<img src="https://img.shields.io/badge/Kali_Linux-557C94?style=for-the-badge&logo=kalilinux&logoColor=white"/>
<img src="https://img.shields.io/badge/License-MIT-blue?style=for-the-badge"/>

<br/>
<br/>

```
███████╗ ██████╗ ██████╗ ████████╗██╗ ██████╗  █████╗ ████████╗███████╗
██╔════╝██╔═══██╗██╔══██╗╚══██╔══╝██║██╔════╝ ██╔══██╗╚══██╔══╝██╔════╝
█████╗  ██║   ██║██████╔╝   ██║   ██║██║  ███╗███████║   ██║   █████╗  
██╔══╝  ██║   ██║██╔══██╗   ██║   ██║██║   ██║██╔══██║   ██║   ██╔══╝  
██║     ╚██████╔╝██║  ██║   ██║   ██║╚██████╔╝██║  ██║   ██║   ███████╗
╚═╝      ╚═════╝ ╚═╝  ╚═╝   ╚═╝   ╚═╝ ╚═════╝ ╚═╝  ╚═╝   ╚═╝   ╚══════╝
                      SECURITY LAB — ASSIGNMENT 02
```

# 🔒 FortiGate NGFW Security Lab
### Advanced Network Security | MS Cybersecurity - NUCES Islamabad

**A complete, hands-on lab for deploying and configuring a FortiGate Next-Generation Firewall in a virtualized enterprise environment covering VM deployment, interface hardening, multi-layer policy implementation, and live threat validation.**

<br/>

[![Stars](https://img.shields.io/github/stars/yourusername/fortigate-security-lab?style=social)](https://github.com/yourusername/fortigate-security-lab)
[![Forks](https://img.shields.io/github/forks/yourusername/fortigate-security-lab?style=social)](https://github.com/yourusername/fortigate-security-lab)
[![Issues](https://img.shields.io/github/issues/yourusername/fortigate-security-lab)](https://github.com/yourusername/fortigate-security-lab/issues)

</div>

---

## 📋 Table of Contents

- [📌 Overview](#-overview)
- [🏗️ Lab Architecture](#️-lab-architecture)
- [⚙️ Prerequisites](#️-prerequisites)
- [🚀 Quick Start](#-quick-start)
- [📦 Task 1 — FortiGate VM Deployment](#-task-1--fortigate-vm-deployment)
  - [Step 1 — Download FortiGate VM](#step-1--download-fortigate-vm)
  - [Step 2 — Configure Virtual Network Interfaces](#step-2--configure-virtual-network-interfaces)
  - [Step 3 — Deploy FortiGate VM in VMware](#step-3--deploy-fortigate-vm-in-vmware)
  - [Step 4 — Configure Management Interface via CLI](#step-4--configure-management-interface-via-cli)
  - [Step 5 — Access FortiGate GUI](#step-5--access-fortigate-gui)
  - [Step 6 — Configure WAN and LAN Interfaces](#step-6--configure-wan-and-lan-interfaces)
  - [Step 7 — Test Connectivity](#step-7--test-connectivity)
- [🔐 Task 2 — GUI Access Configuration](#-task-2--gui-access-configuration)
  - [Step 1 — Enable HTTPS GUI Access](#step-1--enable-https-gui-access)
  - [Step 2 — Configure Admin Credentials](#step-2--configure-admin-credentials)
  - [Step 3 — Verify Login](#step-3--verify-login)
- [🛡️ Task 3 — Policy Implementation](#️-task-3--policy-implementation)
  - [Policy A — IPv4 Firewall Policy](#policy-a--ipv4-firewall-policy)
  - [Policy B — IPv4 DoS Anomaly Protection](#policy-b--ipv4-dos-anomaly-protection)
  - [Policy C — Web Content Filtering](#policy-c--web-content-filtering)
- [🧪 Task 4 — Demonstration & Validation](#-task-4--demonstration--validation)
  - [Website Blocking Test](#website-blocking-test)
  - [DoS Attack Simulation](#dos-attack-simulation)
- [📊 Results Summary](#-results-summary)
- [🔧 Troubleshooting](#-troubleshooting)
- [📁 Repository Structure](#-repository-structure)
- [📚 References](#-references)
- [👤 Author](#-author)

---

## 📌 Overview

This repository documents the complete deployment and configuration of a **FortiGate VM Next-Generation Firewall** within a VMware Workstation virtualized environment as part of the **Advanced Network Security** course (MS Cybersecurity, NUCES Islamabad).

### 🎯 What This Lab Covers

| # | Task | Description | Difficulty |
|---|------|-------------|------------|
| 1 | **VM Deployment** | FortiGate VM provisioning, NIC configuration, CLI setup | 🟡 Intermediate |
| 2 | **GUI Hardening** | HTTPS management, admin credential security | 🟢 Beginner |
| 3 | **Policy Implementation** | IPv4 firewall, DoS protection, web filtering | 🔴 Advanced |
| 4 | **Validation** | Live website blocking and DoS attack testing | 🟡 Intermediate |

### 🔑 Key Technologies

```
FortiGate VM (FortiOS)  ·  VMware Workstation  ·  hping3  ·  Kali Linux
IPv4 Firewall Policies  ·  DoS Anomaly Detection  ·  URL Web Filtering  ·  NAT
```

---

## 🏗️ Lab Architecture

```
                        ┌─────────────────────────────────────────┐
                        │           LAB TOPOLOGY                  │
                        └─────────────────────────────────────────┘

     ┌──────────┐           ┌─────────────────────────────────────────────┐
     │ INTERNET │ ◄────────►│              FortiGate VM                   │
     └──────────┘  WAN/ISP  │         (FortiOS — VMware Workstation)      │
                   port2    │                                             │
                            │  ┌──────────┐  ┌──────────┐  ┌──────────┐  │
                            │  │  port1   │  │  port2   │  │  port3   │  │
                            │  │  (Mgmt)  │  │  (WAN)   │  │  (LAN)   │  │
                            │  └────┬─────┘  └────┬─────┘  └────┬─────┘  │
                            └───────┼─────────────┼─────────────┼────────┘
                                    │             │             │
                         192.168.139.131     ISP Public    Internal
                         (Host-Only)          IP Addr    192.168.x.x/24
                                    │                          │
                             ┌──────┴──────┐          ┌───────┴────────┐
                             │  Admin/Mgmt  │          │  LAN Clients   │
                             │  Workstation │          │  (DHCP Pool)   │
                             └─────────────┘          └────────────────┘
                                                               │
                                                    ┌──────────┴──────────┐
                                                    │   Kali Linux VM     │
                                                    │  (Attacker / Test)  │
                                                    └─────────────────────┘
```

### Virtual Network Adapter Mapping

| VMware NIC | Network Type | Subnet | FortiGate Port | Role |
|------------|-------------|--------|----------------|------|
| VMNet1 | Host-Only | 192.168.40.0/24 | port2 | WAN Simulation |
| VMNet2 | Host-Only | 192.168.50.0/24 | port3 | LAN |
| VMNet3 | Host-Only | Custom | port4 | DMZ (optional) |
| VMNet8 | NAT | VMware NAT | port1 | **Management** |
| VMNet11 | Host-Only | Custom | port5 | Additional Zone |
| VMNet12 | Host-Only | Custom | port6 | Additional Zone |

---

## ⚙️ Prerequisites

### Software Requirements

```bash
# Required
VMware Workstation Pro (v16 or later)     # Hypervisor
FortiGate VM image (FortiGate-VM64.ovf)   # Obtain from Fortinet support portal
Kali Linux VM                             # For DoS testing (Task 4)

# Optional but recommended
7-Zip or WinRAR                           # For extracting FortiGate VM archive
Any modern browser (Chrome, Firefox)     # For FortiGate GUI access
```

### Hardware Requirements

| Resource | Minimum | Recommended |
|----------|---------|-------------|
| Host RAM | 8 GB | 16 GB |
| Host CPU | 4 cores | 8 cores |
| Free Disk | 40 GB | 60 GB |
| FortiGate VM RAM | 1 GB | **2 GB** |
| FortiGate VM vCPU | 1 | 1 |
| FortiGate VM HDD | 30 GB | 30 GB |

### Fortinet Account

> ⚠️ **A Fortinet support portal account is required** to download the FortiGate VM image.  
> Register at: https://support.fortinet.com

---

## 🚀 Quick Start

```bash
# 1. Clone this repository
git clone https://github.com/yourusername/fortigate-security-lab.git
cd fortigate-security-lab

# 2. Review the lab documentation
cat README.md

# 3. Follow tasks in order:
#    Task 1 → Task 2 → Task 3 → Task 4

# 4. Default FortiGate credentials (change immediately!)
#    Username: admin
#    Password: (blank — press Enter on first login)
```

---

## 📦 Task 1 — FortiGate VM Deployment

### Step 1 — Download FortiGate VM

Navigate to the official Fortinet support portal and download the VMware-compatible FortiGate VM image.

**Download URL:** https://support.fortinet.com/support/#/downloads/vm

```
Select: FortiGate → VM Images → VMware ESXi/Workstation → FortiGate-VM64.ovf
```

After downloading, extract the `.zip` archive. You should see:

```
FortiGate-VM64/
├── FortiGate-VM64.ovf       ← OVF descriptor (import this)
├── FortiGate-VM64.mf        ← Manifest (checksums)
├── fortios.vmdk             ← Primary disk image
└── datadrive.vmdk           ← Data disk
```

> 💡 **Tip:** Verify the SHA256 checksum of the downloaded archive against the value published on the Fortinet portal before proceeding.

---

### Step 2 — Configure Virtual Network Interfaces

Open VMware Workstation's **Virtual Network Editor** to create the required host-only network adapters.

**Path:** `Edit → Virtual Network Editor` *(requires Administrator privileges)*

Or search **"Virtual Network Editor"** from the Windows Start Menu.

```
Default networks available:
  VMNet1  →  Host-Only
  VMNet8  →  NAT

Add the following networks (Host-Only type):
  VMNet2  →  192.168.50.0/24    (LAN)
  VMNet3  →  [your choice]      (Additional zone)
  VMNet11 →  [your choice]      (Additional zone)
  VMNet12 →  [your choice]      (Additional zone)
```

**Configuration rules:**
- ✅ Set all new adapters to **Host-Only** mode
- ✅ Assign a **unique, non-overlapping subnet** to each
- ✅ Disable DHCP on adapters (FortiGate will manage addressing)
- ❌ Do NOT use NAT type for interface zones (only for management)

---

### Step 3 — Deploy FortiGate VM in VMware

Import the OVF template into VMware Workstation:

```
VMware Workstation → File → Open (Ctrl+O)
  └── Select: FortiGate-VM64.ovf
      ├── Assign VM Name:    FortiGate-Lab
      └── Storage Path:      [your preferred directory]
```

After import completes, configure VM hardware settings:

**`Edit Virtual Machine Settings` → Set the following:**

| Hardware Component | Value |
|-------------------|-------|
| Memory (RAM) | **2048 MB (2 GB)** |
| Processors | 1 vCPU |
| Hard Disk | 30 GB |
| Network Adapter 1 | VMNet8 (NAT) → port1 Management |
| Network Adapter 2 | VMNet2 (Host-Only) → port2 WAN |
| Network Adapter 3 | VMNet3 (Host-Only) → port3 LAN |
| Network Adapter 4 | VMNet11 (Host-Only) → port4 |
| Network Adapter 5 | VMNet11 (Host-Only) → port5 |
| Network Adapter 6 | VMNet12 (Host-Only) → port6 |

> ⚠️ The OVF import may take **3–10 minutes** depending on disk speed. Do not interrupt the process.

---

### Step 4 — Configure Management Interface via CLI

Boot the FortiGate VM and log in through the VMware console:

```
Login:    admin
Password: [press Enter — blank by default]
          → You will be prompted to set a new password immediately
```

**Verify current interface state:**

```bash
get system interface
```

**Configure port1 as the management interface:**

```bash
config system interface
    edit port1
        set mode static
        set ip 192.168.139.131 255.255.255.0
        set allowaccess http https ssh ping
    next
end
```

**Verify the configuration was applied:**

```bash
show system interface port1
```

Expected output excerpt:
```
config system interface
    edit "port1"
        set ip 192.168.139.131 255.255.255.0
        set allowaccess ping https ssh http
        set type physical
    next
end
```

> 🔐 **Security note:** Remove `http` and `telnet` from `allowaccess` in production. Use only `https` and `ssh`.

---

### Step 5 — Access FortiGate GUI

Test connectivity from your host machine:

```bash
ping 192.168.139.131
```

Expected: replies received → management interface is reachable.

Open a browser and navigate to:

```
https://192.168.139.131
```

> ⚠️ Accept the self-signed certificate warning (expected in lab environments).

**Login credentials:**
```
Username:  admin
Password:  [the password you set in Step 4]
```

**Initial Setup Wizard — recommended settings:**

| Wizard Step | Recommended Action |
|-------------|-------------------|
| Hostname | Set a descriptive name (e.g., `FG-Lab-01`) |
| Password | Already configured — confirm |
| Firmware Upgrade | Optional in lab; recommended in production |
| Dashboard | Select **Optimal** layout |

---

### Step 6 — Configure WAN and LAN Interfaces

Navigate to **Network → Interfaces** in the GUI.

#### WAN Interface (port2)

```
Interface:        port2
Alias:            WAN
Role:             WAN
Addressing Mode:  Manual
IP/Netmask:       [ISP-provided public IP] / [subnet mask]
Admin Access:     HTTPS, PING (minimal)
```

#### LAN Interface (port3)

```
Interface:        port3
Alias:            LAN
Role:             LAN
Addressing Mode:  Manual
IP/Netmask:       192.168.100.1 / 255.255.255.0
DHCP Server:      ✅ Enable
  - IP Range:     192.168.100.10 – 192.168.100.200
  - DNS Server 1: 8.8.8.8
  - DNS Server 2: 8.8.4.4
```

#### Add Default Static Route

**Network → Static Routes → Create New**

```
Destination:  Subnet → 0.0.0.0 / 0.0.0.0
Gateway:      [ISP gateway IP]
Interface:    port2
Distance:     10
```

> This 0.0.0.0/0 default route directs all internet-bound traffic through the WAN interface to the ISP gateway.

---

### Step 7 — Test Connectivity

From a LAN client (or the FortiGate CLI), verify end-to-end internet connectivity:

```bash
# From FortiGate CLI
execute ping 8.8.8.8

# From LAN client
ping 8.8.8.8
tracert 8.8.8.8     # Windows
traceroute 8.8.8.8  # Linux
```

✅ **Expected:** Successful ping replies confirm LAN → FortiGate → WAN routing is operational.

---

## 🔐 Task 2 — GUI Access Configuration

### Step 1 — Enable HTTPS GUI Access

Navigate to **Network → Interfaces → port1 → Edit**

Under **Administrative Access**, confirm the following:

```
☑ HTTPS     ← Required for GUI access
☑ SSH       ← Required for CLI access
☑ PING      ← Required for connectivity testing
☐ HTTP      ← Disable (insecure)
☐ TELNET    ← Disable (insecure, unencrypted)
```

Click **OK** to save.

---

### Step 2 — Configure Admin Credentials

Navigate to **System → Administrators → admin → Edit**

| Setting | Recommended Value |
|---------|-----------------|
| Username | `admin` (or rename for obscurity) |
| Password | Min. 12 chars: uppercase + lowercase + digits + symbols |
| Admin Profile | `super_admin` |
| Trusted Hosts | `192.168.139.0/24` (restrict to management subnet) |
| Two-Factor Auth | Enable FortiToken (recommended for production) |

> 🔐 **Why Trusted Hosts matter:** Even if admin credentials are compromised, an attacker cannot log in from an unauthorized IP address.

---

### Step 3 — Verify Login

1. Log out of the current session
2. Navigate to `https://192.168.139.131`
3. Log in with updated credentials
4. Confirm dashboard loads successfully

✅ **Expected:** Authenticated access to FortiGate dashboard confirms credential update was successful.

---

## 🛡️ Task 3 — Policy Implementation

### Policy A — IPv4 Firewall Policy

**Policy & Objects → Firewall Policy → Create New**

```
Name:                 Internet-Traffic
Incoming Interface:   port3 (LAN)
Outgoing Interface:   port2 (WAN)
Source:               all
Destination:          all
Service:              ALL
Action:               ACCEPT
NAT:                  ✅ Enable
  └── Use Outgoing Interface Address
Logging:              ✅ Enable (Log Allowed Traffic)
```

> This policy implements **Port Address Translation (PAT/masquerade)**, allowing all internal LAN clients to share the single WAN IP address when accessing the internet.

---

### Policy B — IPv4 DoS Anomaly Protection

**Policy & Objects → IPv4 DoS Policy → Create New**

```
Name:                 DoS-Protection-Policy
Incoming Interface:   port2 (WAN)
Source Address:       all
Destination Address:  all
Service:              ALL
```

#### Layer 3 Anomaly Profiles

| Anomaly | Status | Log | Action | Threshold |
|---------|--------|-----|--------|-----------|
| `ip_src_session` | ✅ Enable | ✅ Enable | **Block** | 5000 |
| `ip_dst_session` | ✅ Enable | ✅ Enable | **Block** | 5000 |

#### Layer 4 Anomaly Profiles

| Anomaly | Protocol | Status | Action | Attack Type |
|---------|----------|--------|--------|-------------|
| `tcp_syn_flood` | TCP | ✅ Enable | **Block** | SYN flood / TCP state exhaustion |
| `tcp_port_scan` | TCP | ✅ Enable | **Block** | Port enumeration / reconnaissance |
| `tcp_src_session` | TCP | ✅ Enable | **Block** | Session table exhaustion |
| `tcp_dst_session` | TCP | ✅ Enable | **Block** | Session table exhaustion |
| `udp_flood` | UDP | ✅ Enable | **Block** | UDP amplification flood |
| `udp_scan` | UDP | ✅ Enable | **Block** | UDP port scan |
| `udp_src_session` | UDP | ✅ Enable | **Block** | UDP session exhaustion |
| `udp_dst_session` | UDP | ✅ Enable | **Block** | UDP session exhaustion |
| `icmp_flood` | ICMP | ✅ Enable | **Block** | Ping flood / Smurf attack |
| `icmp_sweep` | ICMP | ✅ Enable | **Block** | Host discovery sweep |
| `icmp_src_session` | ICMP | ✅ Enable | **Block** | ICMP session exhaustion |
| `sctp_flood` | SCTP | ✅ Enable | **Block** | SCTP association flood |
| `sctp_scan` | SCTP | ✅ Enable | **Block** | SCTP port scan |
| `sctp_src_session` | SCTP | ✅ Enable | **Block** | SCTP session exhaustion |
| `sctp_dst_session` | SCTP | ✅ Enable | **Block** | SCTP session exhaustion |

Click **OK** to save the DoS policy.

> 💡 **Threshold Tuning:** Default thresholds may generate false positives in high-traffic environments. Profile baseline traffic before setting production thresholds.

---

### Policy C — Web Content Filtering

#### 1. Enable Web Filter Feature

**System → Feature Visibility**

```
Web Filter:   ✅ Toggle ON → Apply
```

#### 2. Configure URL Filter Profile

**Security Profiles → Web Filter → [default] → Static URL Filter → URL Filter → Create**

```
URL:     facebook.com
Type:    Wildcard          ← Matches *.facebook.com and all subdomains
Action:  Block
Status:  ✅ Enable
```

Click **OK** to save.

> The **Wildcard** type ensures subdomains like `m.facebook.com`, `static.xx.fbcdn.net`, and `connect.facebook.net` are also blocked, preventing evasion.

#### 3. Create Web Filter Firewall Policy

**Policy & Objects → Firewall Policy → Create New**

```
Name:                         No-Facebook-Internet-Access
Incoming Interface:           port3 (LAN)
Outgoing Interface:           port2 (WAN)
Source:                       all
Destination:                  all
Service:                      ALL
Action:                       ACCEPT
NAT:                          ✅ Enable — Use Outgoing Interface Address
Security Profiles:
  └── Web Filter:             ✅ [your web filter profile with facebook block]
```

#### 4. Set Policy Order ⚠️ CRITICAL

**Policy & Objects → Firewall Policy → View By Sequence**

Drag `No-Facebook-Internet-Access` to **position #1** (above `Internet-Traffic`).

```
Policy Evaluation Order:
  [1] No-Facebook-Internet-Access   ← Web filter applied here FIRST
  [2] Internet-Traffic               ← General internet access
  [3] (implicit deny all)
```

> ❗ **If this policy is below `Internet-Traffic`, the web filter will never trigger.** FortiGate evaluates policies top-to-bottom and stops at the first match.

---

## 🧪 Task 4 — Demonstration & Validation

### Website Blocking Test

**From any LAN client browser, navigate to:**

```
https://www.facebook.com
https://m.facebook.com
```

**Expected result:**

```
⛔ Access to the requested website is blocked.
   URL: facebook.com
   Policy: No-Facebook-Internet-Access
   Category: Social Media
```

Verify the block event in **Log & Report → Security Events → Web Filter**

---

### DoS Attack Simulation

Run the following from **Kali Linux** (on a network segment connected to FortiGate):

```bash
# SYN Flood Attack — targets FortiGate management IP
hping3 -c 15000 -d 120 -S -w 64 -p 80 --flood --rand-source 192.168.205.2
```

**Flag breakdown:**

| Flag | Value | Description |
|------|-------|-------------|
| `-c` | `15000` | Total packets to send |
| `-d` | `120` | Data payload size in bytes |
| `-S` | — | Set TCP SYN flag |
| `-w` | `64` | TCP window size |
| `-p` | `80` | Destination port (HTTP) |
| `--flood` | — | Send at maximum rate (no delay) |
| `--rand-source` | — | Randomize source IP (simulates DDoS spoofing) |

**Expected result:**

```bash
# hping3 output — no responses received = traffic is being dropped
HPING 192.168.205.2 (eth0 192.168.205.2): S set, 40+120 headers+data bytes
[main] memlockall(): Success

# FortiGate DoS Policy Log:
Date/Time     | Anomaly        | Action  | Source         | Destination
--------------+----------------+---------+----------------+------------------
[timestamp]   | tcp_syn_flood  | Dropped | [rand IP]      | 192.168.205.2:80
```

Verify in **Log & Report → Security Events → DoS**

---

## 📊 Results Summary

| Task | Test | Expected | Actual | Status |
|------|------|----------|--------|--------|
| Task 1 | FortiGate VM boots & CLI accessible | Login prompt visible | ✅ Login successful | **PASS** |
| Task 1 | Management IP reachable | Ping replies from 192.168.139.131 | ✅ Ping successful | **PASS** |
| Task 1 | LAN client internet access | Ping 8.8.8.8 from LAN | ✅ Internet reachable | **PASS** |
| Task 2 | HTTPS GUI accessible | Dashboard loads | ✅ GUI accessible | **PASS** |
| Task 2 | New credentials work | Login with updated password | ✅ Authentication success | **PASS** |
| Task 3A | IPv4 policy active | Policy visible in table | ✅ Policy enabled | **PASS** |
| Task 3B | DoS policy active | Policy visible in table | ✅ Policy enabled | **PASS** |
| Task 3C | Web filter enabled | Feature visible in GUI | ✅ Feature active | **PASS** |
| Task 4 | facebook.com blocked | Block page displayed | ✅ Access denied | **PASS** |
| Task 4 | SYN flood blocked | hping3 receives no replies | ✅ Traffic dropped | **PASS** |

---

## 🔧 Troubleshooting

<details>
<summary><strong>❓ Cannot access FortiGate GUI after setting IP</strong></summary>

```bash
# Verify the IP was set correctly via CLI
show system interface port1

# Check that allowaccess includes https
# If not, re-run:
config system interface
    edit port1
        set allowaccess https ssh ping
    next
end

# Verify your host machine is on the same subnet
# Host IP should be in 192.168.139.0/24 range
```
</details>

<details>
<summary><strong>❓ Browser shows certificate error for FortiGate GUI</strong></summary>

This is expected. FortiGate uses a self-signed certificate by default.

- **Chrome:** Click **Advanced** → **Proceed to 192.168.139.131 (unsafe)**
- **Firefox:** Click **Advanced** → **Accept the Risk and Continue**
- For production: Install a valid certificate via **System → Certificates**
</details>

<details>
<summary><strong>❓ LAN clients cannot reach the internet</strong></summary>

Check in order:
1. **Default route exists:** Network → Static Routes → verify 0.0.0.0/0 route
2. **IPv4 policy exists:** Policy & Objects → Firewall Policy → verify Internet-Traffic policy
3. **NAT is enabled** on the firewall policy
4. **WAN interface IP is correct** (matches ISP configuration)
5. **DNS is configured:** Network → DNS → set DNS servers (8.8.8.8, 8.8.4.4)
</details>

<details>
<summary><strong>❓ facebook.com is not being blocked</strong></summary>

1. Verify the web filter policy is **at the TOP** of the policy list (By Sequence view)
2. Confirm the web filter profile is **attached** to the policy (Security Profiles section)
3. Check that the URL entry is `facebook.com`, Type `Wildcard`, Action `Block`, Status `Enabled`
4. Clear browser cache and retry (browser may have cached the page)
5. Check FortiGate web filter logs: Log & Report → Security Events → Web Filter
</details>

<details>
<summary><strong>❓ DoS policy is not triggering</strong></summary>

1. Verify the DoS policy interface is set to the **WAN interface** (where attack traffic arrives)
2. Check that the specific anomaly profile (e.g., `tcp_syn_flood`) status is **Enabled**
3. Check that Action is set to **Block** (not Pass)
4. Verify the hping3 command is targeting the correct IP address
5. Check logs: Log & Report → Security Events → DoS
</details>

<details>
<summary><strong>❓ VMware shows import error for FortiGate OVF</strong></summary>

```
Try: File → Open → Browse to .ovf file (not .vmx)
If error persists, use VMware OVFTool:
  ovftool FortiGate-VM64.ovf output/FortiGate-VM64.vmx
```
</details>

---

## 📁 Repository Structure

```
fortigate-security-lab/
│
├── README.md                          ← This file
│
├── docs/
│   ├── FortiGate_Security_Lab_Report.docx   ← Full technical report (PDF-quality)
│   └── Lab_Assignment_Brief.pdf             ← Original assignment brief
│
├── screenshots/
│   ├── task1/
│   │   ├── 01_download_portal.png
│   │   ├── 02_extracted_files.png
│   │   ├── 03_vmnet_editor.png
│   │   ├── 04_privilege_escalation.png
│   │   ├── 05_vmnet_config.png
│   │   ├── 06_ovf_import.png
│   │   ├── 07_vm_name_path.png
│   │   ├── 08_import_progress.png
│   │   ├── 09_vm_settings.png
│   │   ├── 10_nic_allocation.png
│   │   ├── 11_cli_login.png
│   │   ├── 12_get_interface.png
│   │   ├── 13_set_mgmt_ip.png
│   │   ├── 14_show_interface.png
│   │   ├── 15_ping_mgmt.png
│   │   ├── 16_gui_login.png
│   │   ├── 17_setup_wizard.png
│   │   ├── 18_dashboard.png
│   │   ├── 19_interfaces_list.png
│   │   ├── 20_wan_config.png
│   │   ├── 21_lan_config.png
│   │   ├── 22_dhcp_enable.png
│   │   ├── 23_static_routes.png
│   │   ├── 24_default_route.png
│   │   └── 25_connectivity_test.png
│   │
│   ├── task2/
│   │   ├── 01_https_verify.png
│   │   ├── 02_admin_access.png
│   │   ├── 03_administrators_menu.png
│   │   ├── 04_admin_list.png
│   │   ├── 05_edit_admin.png
│   │   ├── 06_login_page.png
│   │   └── 07_login_success.png
│   │
│   ├── task3/
│   │   ├── 01_fw_policy_create.png
│   │   ├── 02_fw_policy_config.png
│   │   ├── 03_nat_enable.png
│   │   ├── 04_policy_saved.png
│   │   ├── 05_dos_policy_l3.png
│   │   ├── 06_dos_l3_thresholds.png
│   │   ├── 07_dos_policy_tcp_udp.png
│   │   ├── 08_dos_policy_icmp_sctp.png
│   │   ├── 09_dos_policy_saved.png
│   │   ├── 10_feature_visibility.png
│   │   ├── 11_webfilter_profile.png
│   │   ├── 12_url_filter.png
│   │   ├── 13_facebook_block_entry.png
│   │   ├── 14_webfilter_policy.png
│   │   ├── 15_security_profile_attach.png
│   │   └── 16_policy_order.png
│   │
│   └── task4/
│       ├── 01_facebook_blocked_browser.png
│       ├── 02_block_page.png
│       ├── 03_block_details.png
│       ├── 04_webfilter_log.png
│       ├── 05_hping3_command.png
│       ├── 06_dos_detection_log.png
│       └── 07_dos_event_detail.png
│
└── configs/
    └── fortigate_baseline.conf        ← Sample FortiGate CLI config export
```

---

## 📚 References

| Resource | URL |
|----------|-----|
| FortiOS Administration Guide | https://docs.fortinet.com/document/fortigate |
| FortiGate VM on VMware Guide | https://docs.fortinet.com/document/fortigate-vm |
| FortiGate DoS Policy Docs | https://docs.fortinet.com/document/fortigate/latest/administration-guide |
| NIST SP 800-41 Rev. 1 — Firewall Guidelines | https://csrc.nist.gov/publications/detail/sp/800-41/rev-1/final |
| NIST SP 800-94 — IDPS Guide | https://csrc.nist.gov/publications/detail/sp/800-94/final |
| hping3 Manual | https://linux.die.net/man/8/hping3 |
| VMware Workstation Documentation | https://docs.vmware.com/en/VMware-Workstation-Pro |
| Fortinet Community Forums | https://community.fortinet.com |

---

## 👤 Author

<div align="center">

| Field | Detail |
|-------|--------|
| **Name** | Sarmad Farooq |
| **Student ID** | 25I-7722 |
| **Program** | MS Cybersecurity |
| **Course** | Advanced Network Security |
| **Instructor** | Dr. Zafar Iqbal |
| **Institution** | NUCES — FAST Islamabad |

</div>

---

<div align="center">

**⭐ If this lab documentation helped you, please star the repository!**

<br/>

Made with 🔒 for the cybersecurity community

<br/>

<img src="https://img.shields.io/badge/FortiGate-Deployed-EE3124?style=flat-square&logo=fortinet"/>
<img src="https://img.shields.io/badge/Policies-Implemented-success?style=flat-square"/>
<img src="https://img.shields.io/badge/DoS-Blocked-blue?style=flat-square"/>
<img src="https://img.shields.io/badge/Facebook-Blocked-red?style=flat-square"/>

</div>
