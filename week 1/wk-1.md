# TechBiz Academy — Ethical Hacking Internship
## Week 1 Submission · Ahmed

> **Internship Provider:** TechBiz Academy  
> **Track:** Ethical Hacking  
> **Week:** 1 (Nov 10 – Nov 16, 2026)  
> **Submitted by:** Ahmed

---

## Overview

This repository contains all three task submissions for Week 1 of the TechBiz Ethical Hacking internship. Each task folder includes a PDF report summarizing the work done and the concepts covered, along with screenshots organized by room/activity.

---

## Task 1 — Ethical Hacking Fundamentals

**Deadline:** Nov 12, 2026 · **Max Score:** 10 pts

**Report:** [`task 1/report1.pdf`](./task%201/report1.pdf)

**Topics covered in the report:**
- CIA Triad (Confidentiality, Integrity, Availability)
- Types of hackers: White Hat, Grey Hat, Black Hat
- 5 phases of ethical hacking: Reconnaissance → Scanning → Gaining Access → Maintaining Access → Covering Tracks
- Penetration Testing vs Vulnerability Assessment

**TryHackMe rooms completed:**
- [x] Cyber Security Careers Overview — [`task 1/Cyber security careers overview/`](./task%201/Cyber%20security%20careers%20overview/)
- [x] Intro to Offensive Security — [`task 1/Intro to Offensive Security/`](./task%201/Intro%20to%20Offensive%20Security/)
- [x] Pentesting Fundamentals — [`task 1/Pentesting Fundamentals/`](./task%201/Pentesting%20Fundamentals/)

---

## Task 2 — Networking Basics

**Deadline:** Nov 14, 2026 · **Max Score:** 10 pts

**Report:** [`task 2/week1_task2_report.pdf`](./task%202/week1_task2_report.pdf)

**Topics covered in the report:**
- IP addressing: IPv4, IPv6, and MAC addresses
- The 7 OSI layers with examples per layer
- 10 common ports and their services (FTP, SSH, Telnet, SMTP, DNS, HTTP, HTTPS, MySQL, RDP)
- TCP vs UDP: connection model, reliability, and use cases

**TryHackMe rooms completed:**
- [x] What is Networking — Flag: `THM{YOU_GOT_ON_TRYHACKME}` — [`task 2/what is networking/`](./task%202/what%20is%20networking/)
- [x] Introductory Networking — [`task 2/Introductory Networking/`](./task%202/Introductory%20Networking/)
- [x] Networking Concepts — [`task 2/networking concepts/`](./task%202/networking%20concepts/)

---

## Task 3 — Lab Setup: VirtualBox + Kali Linux

**Deadline:** Nov 16, 2026 · **Max Score:** 10 pts

**Report:** [`task 3/week1_task3_report.pdf`](./task%203/week1_task3_report.pdf)

**Topics covered in the report:**
- Why set up a hacking lab (isolated virtualized environment)
- VirtualBox installation and Kali Linux VM import
- First boot, login, and running required terminal commands
- VM configuration details (RAM, CPU, storage, NAT networking)

**Lab commands run:**
```bash
whoami       # axmad
ip a         # eth0: 10.0.2.15/24 (NAT)
sudo apt update  # 78 MB fetched, 1588 packages available
```

**Screenshots:**
- Lab setup — [`task 3/kali linux/`](./task%203/kali%20linux/)
- TryHackMe — [`task 3/thm/`](./task%203/thm/)

**TryHackMe room completed:**
- [x] Linux Fundamentals Part 1

---

## Repository Structure

```
week 1/
├── README.md
├── task 1/
│   ├── week1_task1_report.pdf
│   ├── Cyber security careers overview/
│   ├── Intro to Offensive Security/
│   └── Pentesting Fundamentals/
├── task 2/
│   ├── week1_task2_report.pdf
│   ├── what is networking/
│   ├── Introductory Networking/
│   └── networking concepts/
└── task 3/
    ├── week1_task3_report.pdf
    ├── kali linux/
    └── thm/
```

---

## Tools & Platforms Used

| Tool | Purpose |
|------|---------|
| TryHackMe | Hands-on labs and room completion |
| Oracle VirtualBox | Type-2 hypervisor for the hacking lab |
| Kali Linux | Penetration testing OS (pre-built VM image) |
| YouTube | Supplementary learning videos |

---

*TechBiz Academy Ethical Hacking Internship — Week 1*