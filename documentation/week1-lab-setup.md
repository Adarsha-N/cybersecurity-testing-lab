# Week 1 — Cybersecurity Lab Setup Documentation

## 1. Objective

The objective of Week 1 was to build a basic cybersecurity testing environment using Kali Linux and VMware Workstation.

Kali Linux is configured as the attacker machine and will be used for future cybersecurity testing activities.

---

## 2. Lab Environment

| Component | Configuration |
|---|---|
| Hypervisor | VMware Workstation |
| Operating System | Kali Linux |
| Network Type | NAT |
| VMware Network | VMnet8 |
| Network Address | 10.0.0.0/24 |
| Gateway | 10.0.0.1 |
| Kali eth0 | 10.0.0.10/24 |
| Shared Folder | C:\downloads |
| Kali Mount Point | /mnt/hgfs/downloads |

---

## 3. Network Configuration

VMware VMnet8 was configured as a NAT network.

The network configuration used was:

```text
Network:       10.0.0.0/24
Subnet Mask:   255.255.255.0
Gateway:       10.0.0.1
