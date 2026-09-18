# cybersecurity-testing-lab
Cybersecurity testing lab built with Kali Linux and VMware Workstation
# Week 1 — Cybersecurity Testing Lab Setup

## 📌 Overview

This repository contains my Week 1 cybersecurity lab setup.

The objective of this week was to build a basic cybersecurity testing environment using Kali Linux and VMware Workstation.

The lab will be used as a foundation for future cybersecurity testing, attack simulation, monitoring, and security analysis.

---

## 🎯 Week 1 Objectives

- Set up VMware Workstation
- Configure Kali Linux as the attacker machine
- Configure a private lab network
- Configure Internet connectivity
- Enable clipboard and drag-and-drop
- Configure a shared folder between Windows and Kali Linux
- Create a VMware snapshot after completing the setup

---

## 🏗️ Lab Architecture

```text
                    Internet
                       │
                       ▼
              VMware NAT (VMnet8)
                 10.0.0.0/24
                       │
                 Gateway
                  10.0.0.1
                       │
                       ▼
              ┌─────────────────┐
              │   Kali Linux    │
              │    Attacker     │
              ├─────────────────┤
              │ eth0            │
              │ 10.0.0.10/24    │
              ├─────────────────┤
              │ eth1            │
              │ Host-only Lab   │
              └─────────────────┘
                       │
                       ▼
              Future Lab Machines
