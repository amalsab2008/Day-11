# 🛡️ Day 11 - Cyber Security Lab Report

## 🔧 Opening Ubuntu & Kali Linux in VMware and VirtualBox

### ▶️ Using VMware
1. Open **VMware Workstation/Player**.
2. Click on `Open a Virtual Machine`.
3. Locate the `.vmx` file for Ubuntu or Kali Linux.
4. Click **Power on this virtual machine**.

### ▶️ Using VirtualBox
1. Launch **Oracle VirtualBox**.
2. Click `New` or `Import Appliance` to add a VM.
3. Select the `.vdi` or `.ova` file.
4. Click **Start** to boot the virtual machine.

---

## 🌐 Finding IP Addresses with `arp-scan`

### 🔧 Install (if needed)
```bash
sudo apt update
sudo apt install arp-scan
```

### 🔎 Scan Local Network
```bash
sudo arp-scan --interface=eth0 --localnet
```
> Replace `eth0` with your interface name (e.g., `wlan0`, `enp0s3`, etc.)

---

## 🛰️ Port Scanning and Version Detection with `nmap`

### 🔧 Basic Scan
```bash
nmap <target-ip>
```

### 🔍 Version Detection
```bash
nmap -sV <target-ip>
```

### ⚡ Aggressive Scan
```bash
nmap -A <target-ip>
```

---

## 🤖 Automatic Vulnerability Detection with `nmap --script=vuln`

Nmap's `vuln` category contains NSE (Nmap Scripting Engine) scripts to identify known vulnerabilities.

### 🔧 Run Vulnerability Scripts
```bash
nmap --script=vuln <target-ip>
```

This script attempts to detect:
- Misconfigurations
- Known CVEs
- Weak services

Example:
```bash
nmap -sV --script=vuln 192.168.1.10
```

---

## 💣 Exploit Research with `searchsploit`

### 🔧 Manual Search Based on `nmap` Results
```bash
searchsploit <service> <version>
```
**Example:**
```bash
searchsploit ProFTPD 1.3.5
```

### 📂 View Exploit File
```bash
searchsploit -x exploits/unix/remote/15662.txt
```

---

## 🔄 Automated `searchsploit` from `nmap` Scan

### Step 1: Save Nmap Results
```bash
nmap -sV -oX scan.xml <target-ip>
```

### Step 2: Use `searchsploit` to Analyze Services
```bash
searchsploit --nmap scan.xml
```

---

## ✅ Complete Workflow Summary

| Step | Tool | Command |
|------|------|---------|
| 1 | Open VM | VMware / VirtualBox |
| 2 | Find Target IP | `sudo arp-scan --localnet` |
| 3 | Scan Ports | `nmap -sV <ip>` |
| 4 | Find Vulnerabilities | `nmap --script=vuln <ip>` |
| 5 | Identify Exploits | `searchsploit <service> <version>` |
| 6 | Automate Exploit Search | `searchsploit --nmap scan.xml` |

---

