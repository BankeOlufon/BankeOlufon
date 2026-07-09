# 📡 Secure Bratz-Inspired Cyberdeck Camera (ESP32-S3)

## 📌 Project Overview
Designed, built, and secured a custom Bratz-inspired micro-cyberdeck camera unit based on the ESP32-S3 architecture using the ESP-IDF framework.  
This project focuses on mitigating vulnerabilities common to commercial IoT devices: local storage theft, passive wireless tracking, MITM pairing attacks, and physical duress scenarios.

---

## 🎯 Core Areas Covered
- Storage Security & File-Level Encryption  
- Physical Anti-Tamper Controls  
- BLE Privacy & Passive Sniffing Mitigation  
- Secure Wireless Pairing & Transport Layer Security  

---

## 🛠️ Technical Tasks & Functions Performed

### Storage Security
- Implemented AES-256 file-level encryption on FATFS before committing payloads to SD card.  
- Ensured extracted SD cards contained only unreadable ciphertext.  

### Physical Anti-Tamper
- Engineered dual-state authentication with standard PIN vs duress PIN.  
- Duress PIN triggered cryptographic erasure of master keys via `nvs_flash_erase()`.  

### Wireless Privacy
- Configured BLE Resolvable Private Addresses (RPA) to rotate MAC addresses dynamically.  
- Restricted resolution to trusted paired devices with IRK.  

### Secure Pairing & Transport
- Enforced LE Secure Connections with ECDH key exchange and numeric comparison pairing.  
- Streamed images over HTTPS/TLS 1.3 with strict certificate validation.  

---

## 🔐 Security Outcomes
- Prevented local storage theft via encryption.  
- Protected against forced unlock scenarios with duress PIN.  
- Mitigated BLE tracking with dynamic MAC rotation.  
- Secured wireless pairing and data transport with modern cryptography.  

---

## 📚 Skills Demonstrated
- ESP-IDF firmware engineering (C)  
- BLE privacy and secure pairing protocols  
- Cryptographic key management  
- TLS 1.3 secure transport implementation  

---

<!-- ## 📷 Portfolio Artifacts
[Placeholder: Bratz-inspired cyberdeck prototype photo]  
[Placeholder: BLE privacy configuration screenshot]  
-->

---

<!-- ## 📊 Phase Mapping Context
(Not applicable — standalone IoT hardening case study)
-->

---

<!-- ## 📈 Why This Matters to Employers
Demonstrates ability to harden IoT devices against physical, wireless, and cryptographic threats while showcasing creative hardware design.
-->

---

## 🔗 Related Projects
- [Smart Accessibility Navigation Node (Cyber-Physical IoT)](#)  
- [IoT Firmware Reverse Engineering & Vulnerability Research Lab](#)  
- [Arduino Secure RFID Door Lock System](#)  
