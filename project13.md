# 📡 IoT Firmware Reverse Engineering & Vulnerability Research Lab

## 📌 Project Overview
Established a hardware hacking and firmware emulation lab to reverse engineer IoT device operating systems.  
This project demonstrates extraction of firmware binaries, unpacking Linux filesystems, and analyzing them for vulnerabilities such as hardcoded credentials, leaked cryptographic keys, and unsafe binaries. Unlike source code review, this workflow focuses on **compiled binaries and filesystems**, demonstrating practical skills in firmware analysis.

Target firmware: **Tasmota** (open-source IoT firmware for ESP8266/ESP32 smart devices).

---

## 🎯 Core Areas Covered
- **[Firmware Acquisition & Binary Extraction](ca://s?q=Download_Tasmota_firmware)**
- **[Static Analysis of Linux Filesystems](ca://s?q=Inspect_Tasmota_filesystem)**
- **[Vulnerability Discovery](ca://s?q=Find_credentials_in_Tasmota_firmware)**
- **[Dynamic Emulation with QEMU](ca://s?q=Emulate_Tasmota_in_QEMU)**

---

## 🛠️ Technical Workflow

### Phase 1: Setup (15 min)
- Environment: Kali Linux  
- Tools: `binwalk`, `firmware-mod-kit`, `qemu`, `ghidra`, `wireshark`  
- Firmware: Downloaded `tasmota.bin` release from GitHub

### Phase 2: Firmware Extraction (20 min)
- Ran `binwalk -e tasmota.bin` to unpack filesystem  
- Inspected `/etc/passwd`, `/etc/shadow`, and config files  
- Searched for hardcoded MQTT credentials, Wi-Fi SSIDs, TLS keys

### Phase 3: Static Analysis (30 min)
- Imported binaries (e.g., `httpd`, `mqtt`) into Ghidra  
- Identified unsafe functions (`strcpy`, `sprintf`, `gets`)  
- Documented findings for portfolio

### Phase 4: Dynamic Emulation (30 min)
- Determined architecture (`file bin/busybox`) → emulated with QEMU  
- Executed daemons (`httpd`) in sandbox mode  
- Observed traffic with Wireshark/Tcpdump (HTTP/MQTT behavior)

### Phase 5: Wrap-Up (25 min)
- Summarized findings:
  - Hardcoded MQTT credentials in configs  
  - Leaked TLS/SSH keys in extracted files  
  - Unsafe memory functions in binaries  
- Framed workflow as acquisition → extraction → static analysis → dynamic emulation → findings

---

## 🔐 Security Outcomes
- Discovered hardcoded administrative credentials  
- Identified leaked private SSH keys in production images  
- Flagged unsafe memory management functions vulnerable to buffer overflow  
- Validated vulnerabilities through dynamic emulation

---

## 📚 Skills Demonstrated
- **[Firmware reverse engineering](ca://s?q=Use_Binwalk_for_firmware_reverse_engineering)** with Binwalk & FMK  
- **[Static analysis](ca://s?q=Analyze_Tasmota_binaries_in_Ghidra)** with Ghidra  
- **[Dynamic emulation](ca://s?q=Emulate_Tasmota_in_QEMU)** with QEMU  
- **IoT vulnerability research methodology**

---

## Artefacts



