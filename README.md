# 🚀 AutoOpsX

**AutoOpsX** is a comprehensive toolkit of automation scripts designed specifically for IT operations, support, and security professionals. This project focuses on streamlining everyday workflows, proactively monitoring system health, and boosting operational efficiency across Windows, Linux, and cloud environments.

Whether you’re managing servers, workstations, or cloud instances, AutoOpsX helps you keep your finger on the pulse — with real-time alerts, detailed logs, and customizable thresholds.

---

## 🔎 Why AutoOpsX?

In the fast-paced world of IT, waiting for problems to surface is a luxury we can’t afford. AutoOpsX empowers you to:

- **Detect issues early:** CPU, memory, and disk usage are monitored continuously, so you catch problems before users do.
- **Stay informed:** Friendly emoji alerts and detailed logs keep you updated in real time.
- **Reduce downtime:** Automated monitoring means less manual checking and faster response times.
- **Operate cross-platform:** Designed to work seamlessly on both Windows and Linux systems.

---

## 📋 Features & Capabilities

- **CPU Monitoring:** Tracks processor usage every second and alerts when usage spikes above 85%.
- **Memory Usage Checks:** Keeps tabs on system RAM, warning if usage surpasses 80%.
- **Disk Space Surveillance:** Watches the root partition and notifies you when disk usage exceeds 90%.
- **Comprehensive System Info:** Logs platform details, processor info, Python version, and timestamp for every run.
- **Robust Logging:** All metrics and alerts are recorded in `autoopsx_health.log` for audit trails and troubleshooting.
- **Clear Alerts:** Uses emojis and concise messages to make monitoring less boring and more actionable.
- **Exception Handling:** Catches and logs fatal errors gracefully, avoiding silent failures.

---

## 🛠️ Installation & Setup Guide

### Prerequisites

- **Python 3.6+** installed on your machine  
- The Python library **psutil**, which provides system and process utilities

### Step 1: Clone the Repository

```bash
git clone https://github.com/yourusername/AutoOpsX.git
cd AutoOpsX