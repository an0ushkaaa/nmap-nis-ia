# Nmap: Network Mapper — NIS Internal Assessment

## Overview
This repository contains the demonstration and results for the Network Information Security (NIS) Internal Assessment on **Nmap (Network Mapper)** — an open-source tool used for network discovery, port scanning, service detection, and vulnerability analysis.

---

## Environment
| Detail | Value |
|---|---|
| Tool | Nmap 7.99 |
| Interface | Zenmap (GUI) |
| Target IP | 10.0.22.14 |
| Target OS | Windows 11 24H2 |
| Network | College LAN |

---

## Commands Demonstrated

### Host Discovery & Port Scanning
| Command | Purpose |
|---|---|
| `nmap -sn 10.0.22.0/24` | Ping scan — find live hosts on subnet |
| `nmap -sS 10.0.22.14` | TCP SYN stealth scan |
| `nmap -sT 10.0.22.14` | TCP Connect scan |
| `nmap -p 22,80,443 10.0.22.14` | Targeted port scan |
| `nmap -sS -oA results -v 10.0.22.14` | Verbose scan with saved output |

### Service & OS Detection
| Command | Purpose |
|---|---|
| `nmap -sV 10.0.22.14` | Service version detection |
| `nmap -O 10.0.22.14` | OS fingerprinting |
| `nmap -A 10.0.22.14` | Aggressive scan (all-in-one) |
| `nmap -T4 10.0.22.14` | Timing template demonstration |

### NSE Scripts & Evasion
| Command | Purpose |
|---|---|
| `nmap -sC 10.0.22.14` | Default NSE scripts |
| `nmap --script=vuln 10.0.22.14` | Vulnerability scan (CVE detection) |
| `nmap -D RND:5 10.0.22.14` | Decoy scan — evasion |
| `nmap -f --source-port 53 10.0.22.14` | Fragmentation + source port spoofing |

---

## Results Summary
- **Live hosts found:** 20 out of 256 IPs on subnet
- **Open ports on target:** 3 (135/msrpc, 139/netbios-ssn, 445/microsoft-ds)
- **OS detected:** Microsoft Windows 11 24H2
- **CVEs tested:** 3 (ms10-054, ms10-061, cve-2012-1182) — all negative on patched machine
- **Output files:** results.nmap, results.xml, results.gnmap

---

## Repository Structure
```
nmap-nis-ia/
├── README.md
├── commands.md
├── results/
   ├── results.nmap
   ├── results.xml
   └── results.gnmap

```

---
