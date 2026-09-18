\# Module 5 — Network Scanning with Zenmap/Nmap



\## 1. Objective



The objective of this module is to understand and perform basic network scanning using \*\*Nmap and Zenmap on Windows\*\*.



The lab focuses on identifying active hosts in a network and understanding how network scanning can be used during reconnaissance and security assessment.



\---



\## 2. Environment



| Component        | Details                           |

| ---------------- | --------------------------------- |

| Operating System | Windows                           |

| Scanning Tool    | Nmap                              |

| GUI Tool         | Zenmap                            |

| Network          | Local Windows network             |

| Scan Type        | Host discovery / Network scanning |

| Purpose          | Authorized cybersecurity lab      |



\---



\## 3. Network Information



The Windows system was checked using the `ipconfig` command.



The system had the following relevant network interfaces:



\* VMware VMnet1: `192.168.111.1/24`

\* VMware VMnet8: `10.0.0.1/24`

\* Wi-Fi: `10.221.30.46/24`



The Wi-Fi network used for the network discovery exercise was:



```text

10.221.30.0/24

```



\---



\## 4. Task 1 — Identify the Windows Network Configuration



The Windows Command Prompt was used to identify the configured network interfaces and IP addresses.



Command used:



```cmd

ipconfig

```



The command displayed the available network adapters, IPv4 addresses, subnet masks and default gateway information.



\### Observation



The Windows machine was connected to the `10.221.30.0/24` network through the Wi-Fi adapter.



\---



\## 5. Task 2 — Network Discovery Using Zenmap



Zenmap was used to perform network discovery on the authorized local network.



Target:



```text

10.221.30.0/24

```



The scan was used to identify active hosts in the network.



\### Result



The scan identified two active hosts:



```text

10.221.30.123

10.221.30.46

```



The scan output showed:



```text

Nmap done: 256 IP addresses (2 hosts up)

```



\### Observation



Out of the 256 addresses in the `/24` network, Nmap identified \*\*2 hosts as active\*\* during the scan.



\---



\## 6. Task 3 — Analyze the Scan Result



The discovered hosts included:



| IP Address      | Status     |

| --------------- | ---------- |

| `10.221.30.123` | Host is up |

| `10.221.30.46`  | Host is up |



The scan also displayed a MAC address for one discovered host:



```text

B2:04:72:79:FF:5F

```



The manufacturer was reported as:



```text

Unknown

```



\### Observation



Host discovery helps a security analyst understand which systems are currently reachable on a network before performing further authorized security assessment.



\---



\## 7. Tools Used



\### Nmap



Nmap is a network discovery and security auditing tool used to:



\* Discover hosts

\* Identify open ports

\* Detect services

\* Perform network reconnaissance

\* Assist with security assessments



\### Zenmap



Zenmap is the graphical interface for Nmap.



It provides a convenient way to:



\* Configure scans

\* Enter targets

\* Select scan profiles

\* View scan results

\* Save and review scan information



\---



\## 8. Security Relevance



Network scanning is an important activity during the reconnaissance phase of a security assessment.



A SOC analyst or security professional can use authorized scanning results to understand:



\* Which hosts are active

\* Which systems may require monitoring

\* What services are exposed

\* Whether unexpected systems are present

\* Potential areas that require further investigation



Network scanning should only be performed on systems and networks where permission has been granted.



\---



\## 9. Evidence / Screenshots



The screenshots for this module are stored in:



```text

screenshots/

```



The screenshots demonstrate the Windows network configuration and Zenmap/Nmap scanning activities performed during the lab.



\---



\## 10. Key Learning Outcomes



After completing this module, I learned:



1\. How to identify Windows network configuration using `ipconfig`.

2\. How to identify the active network and subnet.

3\. How to perform network discovery using Zenmap/Nmap.

4\. How to identify active hosts in a `/24` network.

5\. How to interpret basic Nmap scan output.

6\. The importance of network reconnaissance in cybersecurity.

7\. How network scanning can support security monitoring and assessment.



\---



\## 11. Conclusion



Module 5 provided practical experience with \*\*network discovery and scanning using Zenmap/Nmap on Windows\*\*.



The scan of the authorized `10.221.30.0/24` network identified two active hosts. This exercise helped build a practical understanding of host discovery, Nmap results and the role of network reconnaissance in cybersecurity.



This module forms a foundation for more advanced security activities such as service enumeration, vulnerability assessment and SOC investigation.



