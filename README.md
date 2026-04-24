# Endpoint Security & Data Loss Prevention (DLP) System

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Platform](https://img.shields.io/badge/platform-Windows-lightgrey.svg)
![Language](https://img.shields.io/badge/language-C%23%20%7C%20ASP.NET-green.svg)

## 📌 Project Overview
The **Endpoint Security & Data Loss Prevention (DLP) System** is a proactive security solution designed to mitigate internal data breaches. It monitors organizational workstations for unauthorized hardware interactions—specifically the insertion of third-party storage devices like Pen Drives or External Hard Disks. 

When an unauthorized device is detected, the system executes an immediate defensive response (System Shutdown/Logout) and notifies administrators in real-time to prevent data exfiltration.

> **Note:** This project was originally developed under the title *"Automatic System Logged at File Hacking System"* and has since been rebranded to align with industry-standard cybersecurity terminology.

---

## ✨ Key Features
- **Automated Threat Mitigation:** Programmed an event-driven trigger that detects USB/HDD insertion, forcing an automatic system shutdown or logout to block unauthorized file transfers.
- **Instant Admin Notifications:** Integrated SMTP protocols to send real-time email alerts to administrators, including timestamps and device details for immediate incident response.
- **Access Management:** Architected a Role-Based Access Control (RBAC) framework with separate modules for Admin oversight and Employee task allotment.
- **System Auditing:** Built a background logging engine to track file distribution and monitor workspace activity across the network.

---

## 🛠️ Tech Stack
- **Programming Language:** C#
- **Web Framework:** ASP.NET
- **Backend Logic:** .NET Framework
- **Communication:** SMTP (Simple Mail Transfer Protocol) for automated alerting.
- **System Integration:** Windows System APIs & WMI.

---

## 🏗️ System Architecture
1. **Detection:** The system listens for `Win32_DeviceChangeEvent`.
2. **Verification:** It identifies if the new device is a "Mass Storage" class.
3. **Action:** - Calls `ExitWindowsEx` or `Process.Start` to initiate shutdown.
   - Triggers an asynchronous SMTP thread to alert the Admin.
4. **Logging:** Details are written to a secure database/log file for later review.

---

## 🚀 Getting Started

### Prerequisites
- Visual Studio (2019 or newer recommended)
- .NET Framework 4.7.2+
- Administrator privileges (Required for system-level triggers)

### Implementation 

- USB Detection: Mention if you used ManagementEventWatcher or WMI (Windows Management Instrumentation) to listen for hardware changes.
- System Commands: Mention the use of Process.Start("shutdown", "/s /t 0") for the automated power-off.
- Security: Explain why the Admin module is closed-source (to prevent employees from tampering with the monitoring logic).

### How to Use (Step-by-Step)

- Run the Admin module and log in.
- Allot files to the specific employee directory.
- Launch the Employee monitoring service.
- Insert a USB drive to test the automated trigger.

## Future Enhancements
Encryption: Automatically encrypting files before sending them to employees.
USB Whitelisting: Allowing specific "safe" USBs while blocking others.
Cloud Logging: Uploading logs to a cloud database instead of just local storage.
