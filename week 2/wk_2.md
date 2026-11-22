# TechBiz Ethical Hacking Internship — Week 2

> **Track:** Ethical Hacking | **Intern:** Ahmed | **Period:** Week 2

---

## Overview

Week 2 covers the practical foundations of ethical hacking: reconnaissance using network tools, DNS and HTTP analysis, and setting up a real vulnerable lab environment for hands-on exploitation practice. Each task builds on the last — from scanning and enumeration (Task 4) to protocol-level analysis (Task 5) to deploying an actual attack-and-target VM pair (Task 6).

---

## Task 4 — Reconnaissance & Information Gathering

**Deadline:** Nov 19, 2026 · 10:00 PM PKT

### What I Did
Performed passive and active reconnaissance on a target using industry-standard tools. The goal was to gather as much information as possible without triggering alarms — the first phase of any real penetration test.

### Tools Covered

| Tool | Purpose |
|------|---------|
| `whois` | Domain registration info — registrar, owner, name servers, expiry |
| `nmap` | Network scanner — host discovery, open ports, service/version detection, OS fingerprinting |
| `theHarvester` | OSINT harvesting — emails, subdomains, IPs from public sources |
| `Shodan` | Search engine for internet-exposed devices and services |
| `Maltego` | Graph-based OSINT — visualizes relationships between domains, IPs, emails |
| `Recon-ng` | Modular framework for automated web reconnaissance |

### Key Concepts
- **Passive recon** — gathering info without touching the target (WHOIS, Shodan, theHarvester)
- **Active recon** — directly probing the target (nmap scans, DNS queries)
- **Footprinting** — first phase of the ethical hacking kill chain; defines attack surface
- **nmap flags:** `-sV` (version), `-O` (OS), `-A` (aggressive), `-p-` (all ports), `--script` (NSE scripts)

### TryHackMe Rooms Completed
- Passive Reconnaissance — 100%
- Active Reconnaissance — 100%

---

## Task 5 — Networking Tools & Subnetting

**Deadline:** Nov 21, 2026 · 10:00 PM PKT

### What I Did
Used core networking diagnostic tools to analyze connectivity, trace packet routes, and query DNS records. Also worked through subnetting — calculating network ranges, usable hosts, and broadcast addresses from CIDR notation.

### Tools Covered

| Tool | Command | Purpose |
|------|---------|---------|
| `ping` | `ping -c 4 <host>` | ICMP echo — confirms host is up, measures RTT |
| `traceroute` | `traceroute <host>` | Shows each hop between source and destination |
| `nslookup` | `nslookup <domain>` | Queries DNS for A, MX, NS records |
| `dig` | `dig <domain> ANY` | Detailed DNS query with TTL, authority section |
| `netstat` | `netstat -tuln` | Active connections, listening ports, routing table |

### Subnetting Example

Network: `192.168.1.0/24`

| Field | Value |
|-------|-------|
| Subnet Mask | 255.255.255.0 |
| Network Address | 192.168.1.0 |
| Broadcast Address | 192.168.1.255 |
| Usable Host Range | 192.168.1.1 – 192.168.1.254 |
| Total Usable Hosts | 254 |

### TryHackMe Rooms Completed
- DNS in Detail — 100%
- HTTP in Detail — 100%

---

## Task 6 — Vulnerable Lab Setup

**Deadline:** Nov 23, 2026 · 10:00 PM PKT

### What I Did
Set up a fully isolated penetration testing lab using Oracle VirtualBox with two virtual machines: Kali Linux as the attacker and Metasploitable 2 as the target. Configured dual-NIC networking so Kali has internet access while both VMs can communicate privately. Confirmed connectivity with a ping test, then completed the TryHackMe DVWA room including a live file upload exploit.

### Lab Architecture

```
Host Machine
├── Kali Linux (Attacker)
│   ├── Adapter 1: NAT  →  eth0  →  10.0.2.x  (internet via host)
│   └── Adapter 2: Host-only  →  eth1  →  192.168.56.101
│
└── Metasploitable 2 (Target)
    └── Adapter 1: Host-only  →  eth0  →  192.168.56.105  (no internet)
```

Both VMs are on the same `192.168.56.0/24` host-only network. Metasploitable has no NAT adapter — it cannot reach the internet, keeping the lab safely isolated.

### Metasploitable 2 — Vulnerable Services

| Service | Port(s) | Vulnerability |
|---------|---------|---------------|
| vsftpd 2.3.4 | 21 | Backdoor — opens shell on port 6200 |
| OpenSSH 4.7p1 | 22 | Outdated version; weak default credentials |
| Apache 2.2.8 | 80 | Hosts DVWA, phpMyAdmin, Mutillidae |
| Samba 3.0.20 | 139, 445 | MS-RPC usermap_script → remote root shell |
| Tomcat 5.5 | 8180 | Default admin:admin; WAR deployment RCE |
| MySQL 5.0.51a | 3306 | No root password; full DB access |

### Connectivity Test — ping Results

```
ping -c 4 192.168.56.105
```

| Field | Result |
|-------|--------|
| Target IP | 192.168.56.105 |
| Packets sent / received | 4 / 4 |
| Packet loss | 0% |
| RTT min / avg / max | 0.937 / 2.980 / 8.574 ms |
| TTL | 64 (Linux confirmed) |

### TryHackMe — DVWA Room

**Room:** [tryhackme.com/room/dvwa](https://tryhackme.com/room/dvwa) | **Completion: 100%**

DVWA (Damn Vulnerable Web Application) is a PHP/MySQL app built for practising web application attacks legally. Modules include SQL Injection, XSS (DOM/Reflected/Stored), Command Injection, File Upload, Brute Force, CSRF, and File Inclusion.

**File Upload Exploit (demonstrated):**
- Security level: Low
- Uploaded a PHP reverse shell renamed to `shell.phtml`
- Server returned: `../../hackable/uploads/shell.phtml successfully uploaded!`
- The `.php` extension was blocked; `.phtml` bypassed the filter — a real-world bypass technique

---

## What I Learned — Week 2 Summary

| Task | Key Takeaway |
|------|-------------|
| Task 4 | Reconnaissance is the most important phase — the more you know before touching the target, the more precise and stealthy the attack can be |
| Task 4 | Passive recon (WHOIS, Shodan) leaves no trace; active recon (nmap) can trigger IDS/IPS |
| Task 5 | TTL in ping responses reveals the target OS: Linux = 64, Windows = 128 |
| Task 5 | `dig` gives far more detail than `nslookup` — authority section, TTLs, query time |
| Task 5 | Subnetting is fundamental to understanding network segmentation and attack scope |
| Task 6 | A vulnerable lab must never be internet-exposed — Metasploitable warns on boot |
| Task 6 | Dual-NIC setup (NAT + Host-only) is the correct way to give Kali both internet and lab access |
| Task 6 | Extension blocklists are weak file upload protection — `.phtml`, `.php5`, `.phar` often bypass them |
| Task 6 | Isolated lab networks mirror VLAN segmentation used in real corporate environments |

---

## Deliverables

| Task | Report File | Status |
|------|------------|--------|
| Task 4 | `report 1.pdf` | Submitted |
| Task 5 | `report 2.pdf` | Submitted |
| Task 6 | `report 3.pdf` | Submitted |

---

*Ahmed · TechBiz Internship — Ethical Hacking · Week 2*
