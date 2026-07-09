# 📡 IoT Firmware Reverse Engineering & Vulnerability Research Lab

## 📌 Project Overview
Established a hardware hacking and firmware emulation lab to reverse engineer IoT device operating systems.  
This project demonstrates extraction of firmware binaries, unpacking Linux filesystems, and analyzing them for vulnerabilities such as hardcoded credentials, leaked cryptographic keys, and unsafe binaries.

---

## 🎯 Core Areas Covered
- Firmware Acquisition & Binary Extraction  
- Static Analysis of Linux Filesystems  
- Vulnerability Discovery (Credentials, Keys, Unsafe Functions)  
- Dynamic Emulation with QEMU  

---

## 🛠️ Technical Tasks & Functions Performed

### Reverse Engineering Workflow
- Acquired firmware binaries from vendor sites.  
- Used Binwalk to extract SquashFS/CramFS filesystems.  
- Audited `/etc/shadow` and `/etc/passwd` for hardcoded credentials.  
- Scanned directories for leaked cryptographic keys.  
- Imported binaries into Ghidra to identify unsafe memory functions.  

### Dynamic Emulation
- Emulated target architectures (MIPS/ARM) in QEMU.  
- Executed extracted daemons in sandbox to observe traffic handling.  

---

## 🔐 Security Outcomes
- Discovered hardcoded administrative credentials.  
- Identified leaked private SSH keys in production images.  
- Flagged unsafe memory management functions vulnerable to buffer overflow.  
- Validated vulnerabilities through dynamic emulation.  

---

## 📚 Skills Demonstrated
- Firmware reverse engineering with Binwalk & FMK  
- Static analysis with Ghidra/IDA Pro  
- Dynamic emulation with QEMU  
- IoT vulnerability research methodology  

---

<!-- ## 📷 Portfolio Artifacts
[Placeholder: Binwalk extraction output]  
[Placeholder: Ghidra decompiled binary screenshot]  
-->

---

<!-- ## 📈 Why This Matters to Employers
Demonstrates ability to reverse engineer IoT firmware, identify vulnerabilities, and emulate systems for safe testing.
-->

---

## 🔗 Related Projects
- [Hardened IoT Media Deck (ESP32-S3)](#)  
- [Smart Accessibility Navigation Node (Cyber-Physical IoT)](#)  
- [Arduino Secure RFID Door Lock System](#)  
