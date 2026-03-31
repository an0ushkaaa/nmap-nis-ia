# Nmap Commands & Outputs

All scans performed on target `10.0.22.14` (Windows 11 24H2) on college LAN using Nmap 7.99.

---

## Host Discovery & Port Scanning

### 1. Ping Scan
```
nmap -sn 10.0.22.0/24
```
**Output:**
```
Starting Nmap 7.99 ( https://nmap.org ) at 2026-03-31 10:24 +0530
Nmap scan report for 10.0.22.9
Host is up (0.48s latency).
MAC Address: 56:A1:E0:82:5F:EF (Unknown)
Nmap scan report for 10.0.22.19
Host is up (0.20s latency).
MAC Address: 32:68:32:94:09:F8 (Unknown)
Nmap scan report for 10.0.22.32
Host is up (0.011s latency).
MAC Address: AA:FE:D2:A9:E1:56 (Unknown)
Nmap scan report for 10.0.22.38
Host is up (0.61s latency).
MAC Address: 06:1E:7F:F1:2E:6E (Unknown)
Nmap scan report for 10.0.22.43
Host is up (0.26s latency).
MAC Address: 86:72:F9:AC:E6:6D (Unknown)
Nmap scan report for 10.0.22.57
Host is up (0.66s latency).
MAC Address: 86:40:6A:0E:0E:FF (Unknown)
Nmap scan report for 10.0.22.59
Host is up (0.062s latency).
MAC Address: 7E:D2:CC:AF:0F:4F (Unknown)
Nmap scan report for 10.0.22.69
Host is up (0.45s latency).
MAC Address: 7E:55:9F:03:C6:15 (Unknown)
Nmap scan report for 10.0.22.78
Host is up (1.1s latency).
MAC Address: 02:8B:28:DB:31:13 (Unknown)
Nmap scan report for 10.0.22.82
Host is up (0.030s latency).
MAC Address: 14:B5:CD:14:1A:4F (Liteon Technology)
Nmap scan report for 10.0.22.84
Host is up (0.075s latency).
MAC Address: E8:65:38:19:BB:6F (Cloud Network Technology Singapore PTE.)
Nmap scan report for 10.0.22.85
Host is up (0.029s latency).
MAC Address: 16:62:77:A4:64:1C (Unknown)
Nmap scan report for 10.0.22.133
Host is up (0.0070s latency).
MAC Address: 72:C3:A9:55:D0:50 (Unknown)
Nmap scan report for 10.0.22.142
Host is up (0.25s latency).
MAC Address: 14:D4:24:93:1D:EB (AzureWave Technology)
Nmap scan report for 10.0.22.147
Host is up (0.92s latency).
MAC Address: 5A:56:A9:0D:98:FB (Unknown)
Nmap scan report for 10.0.22.165
Host is up (0.088s latency).
MAC Address: 10:91:D1:F0:6C:3E (Intel Corporate)
Nmap scan report for 10.0.22.200
Host is up (1.1s latency).
MAC Address: 92:56:A4:CE:72:35 (Unknown)
Nmap scan report for 10.0.22.239
Host is up (2.0s latency).
MAC Address: 56:7D:E0:48:1B:92 (Unknown)
Nmap scan report for 10.0.22.245
Host is up (1.1s latency).
MAC Address: 70:15:FB:6A:0D:8D (Intel Corporate)
Nmap scan report for 10.0.22.14
Host is up.
Nmap done: 256 IP addresses (20 hosts up) scanned in 19.43 seconds
```

---

### 2. TCP SYN Scan
```
nmap -sS 10.0.22.14
```
**Output:**
```
Starting Nmap 7.99 ( https://nmap.org ) at 2026-03-31 10:25 +0530
Nmap scan report for 10.0.22.14
Host is up (0.00029s latency).
Not shown: 997 closed tcp ports (reset)
PORT    STATE SERVICE
135/tcp open  msrpc
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
Nmap done: 1 IP address (1 host up) scanned in 0.78 seconds
```

---

### 3. TCP Connect Scan
```
nmap -sT 10.0.22.14
```
**Output:**
```
Starting Nmap 7.99 ( https://nmap.org ) at 2026-03-31 10:26 +0530
Nmap scan report for 10.0.22.14
Host is up (0.00073s latency).
Not shown: 997 closed tcp ports (conn-refused)
PORT    STATE SERVICE
135/tcp open  msrpc
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
Nmap done: 1 IP address (1 host up) scanned in 0.79 seconds
```

---

### 4. Targeted Port Scan
```
nmap -p 22,80,443 10.0.22.14
```
**Output:**
```
Starting Nmap 7.99 ( https://nmap.org ) at 2026-03-31 10:27 +0530
Nmap scan report for 10.0.22.14
Host is up (0.00s latency).
PORT    STATE  SERVICE
22/tcp  closed ssh
80/tcp  closed http
443/tcp closed https
Nmap done: 1 IP address (1 host up) scanned in 0.76 seconds
```

---

### 5. Verbose Scan with Saved Output
```
nmap -sS -oA results -v 10.0.22.14
```
**Output:**
```
Starting Nmap 7.99 ( https://nmap.org ) at 2026-03-31 10:28 +0530
Initiating Parallel DNS resolution of 1 host. at 10:28
Completed Parallel DNS resolution of 1 host. at 10:28, 0.51s elapsed
Initiating SYN Stealth Scan at 10:28
Scanning 10.0.22.14 [1000 ports]
Discovered open port 445/tcp on 10.0.22.14
Discovered open port 135/tcp on 10.0.22.14
Discovered open port 139/tcp on 10.0.22.14
Completed SYN Stealth Scan at 10:28, 0.07s elapsed (1000 total ports)
Nmap scan report for 10.0.22.14
Host is up (0.00012s latency).
Not shown: 997 closed tcp ports (reset)
PORT    STATE SERVICE
135/tcp open  msrpc
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
Read data files from: C:\Program Files (x86)\Nmap
Nmap done: 1 IP address (1 host up) scanned in 0.81 seconds
           Raw packets sent: 1000 (44.000KB) | Rcvd: 2003 (84.132KB)
```

---

## Service & OS Detection

### 6. Version Detection
```
nmap -sV 10.0.22.14
```
**Output:**
```
Starting Nmap 7.99 ( https://nmap.org ) at 2026-03-31 10:29 +0530
Nmap scan report for 10.0.22.14
Host is up (0.00029s latency).
Not shown: 997 closed tcp ports (reset)
PORT    STATE SERVICE       VERSION
135/tcp open  msrpc         Microsoft Windows RPC
139/tcp open  netbios-ssn   Microsoft Windows netbios-ssn
445/tcp open  microsoft-ds?
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows
Nmap done: 1 IP address (1 host up) scanned in 7.81 seconds
```

---

### 7. OS Fingerprinting
```
nmap -O 10.0.22.14
```
**Output:**
```
Starting Nmap 7.99 ( https://nmap.org ) at 2026-03-31 10:30 +0530
Nmap scan report for 10.0.22.14
Host is up (0.00029s latency).
Not shown: 997 closed tcp ports (reset)
PORT    STATE SERVICE
135/tcp open  msrpc
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
Device type: general purpose
Running: Microsoft Windows 11
OS CPE: cpe:/o:microsoft:windows_11
OS details: Microsoft Windows 11 24H2 - 25H2
Network Distance: 0 hops
Nmap done: 1 IP address (1 host up) scanned in 2.91 seconds
```

---

### 8. Aggressive Scan
```
nmap -A 10.0.22.14
```
**Output:**
```
Starting Nmap 7.99 ( https://nmap.org ) at 2026-03-31 10:31 +0530
Nmap scan report for 10.0.22.14
Host is up (0.00062s latency).
Not shown: 997 closed tcp ports (reset)
PORT    STATE SERVICE       VERSION
135/tcp open  msrpc         Microsoft Windows RPC
139/tcp open  netbios-ssn   Microsoft Windows netbios-ssn
445/tcp open  microsoft-ds?
Device type: general purpose
Running: Microsoft Windows 11
OS CPE: cpe:/o:microsoft:windows_11
OS details: Microsoft Windows 11 24H2 - 25H2
Network Distance: 0 hops
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows
Host script results:
| smb2-time:
|   date: 2026-03-31T05:01:31
|_  start_date: N/A
| smb2-security-mode:
|   3.1.1:
|_    Message signing enabled and required
Nmap done: 1 IP address (1 host up) scanned in 22.81 seconds
```

---

### 9. Timing Template
```
nmap -T4 10.0.22.14
```
**Output:**
```
Starting Nmap 7.99 ( https://nmap.org ) at 2026-03-31 10:32 +0530
Nmap scan report for 10.0.22.14
Host is up (0.00076s latency).
Not shown: 997 closed tcp ports (reset)
PORT    STATE SERVICE
135/tcp open  msrpc
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
Nmap done: 1 IP address (1 host up) scanned in 0.80 seconds
```

---

## NSE Scripts & Evasion

### 10. Default NSE Scripts
```
nmap -sC 10.0.22.14
```
**Output:**
```
Starting Nmap 7.99 ( https://nmap.org ) at 2026-03-31 10:09 +0530
Nmap scan report for 10.0.22.14
Host is up (0.00014s latency).
Not shown: 997 closed tcp ports (reset)
PORT    STATE SERVICE
135/tcp open  msrpc
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
Host script results:
| smb2-security-mode:
|   3.1.1:
|_    Message signing enabled and required
| smb2-time:
|   date: 2026-03-31T04:39:13
|_  start_date: N/A
Nmap done: 1 IP address (1 host up) scanned in 18.28 seconds
```

---

### 11. Vulnerability Scan
```
nmap --script=vuln 10.0.22.14
```
**Output:**
```
Starting Nmap 7.99 ( https://nmap.org ) at 2026-03-31 10:15 +0530
Nmap scan report for 10.0.22.14
Host is up (0.00s latency).
Not shown: 997 closed tcp ports (reset)
PORT    STATE SERVICE
135/tcp open  msrpc
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
Host script results:
|_smb-vuln-ms10-054: false
|_smb-vuln-ms10-061: Could not negotiate a connection:SMB: Failed to receive bytes: ERROR
|_samba-vuln-cve-2012-1182: Could not negotiate a connection:SMB: Failed to receive bytes: ERROR
Nmap done: 1 IP address (1 host up) scanned in 27.53 seconds
```

---

### 12. Decoy Scan
```
nmap -D RND:5 10.0.22.14
```
**Output:**
```
Starting Nmap 7.99 ( https://nmap.org ) at 2026-03-31 10:16 +0530
Nmap scan report for 10.0.22.14
Host is up (0.0016s latency).
Not shown: 997 closed tcp ports (reset)
PORT    STATE SERVICE
135/tcp open  msrpc
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
Nmap done: 1 IP address (1 host up) scanned in 1.02 seconds
```

---

### 13. Fragmentation + Source Port Spoofing
```
nmap -f --source-port 53 10.0.22.14
```
**Output:**
```
Warning: Packet fragmentation selected on a host other than Linux, OpenBSD, FreeBSD, or NetBSD. This may or may not work.
Starting Nmap 7.99 ( https://nmap.org ) at 2026-03-31 10:17 +0530
Nmap scan report for 10.0.22.14
Host is up.
All 1000 scanned ports on 10.0.22.14 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
Nmap done: 1 IP address (1 host up) scanned in 203.22 seconds
```