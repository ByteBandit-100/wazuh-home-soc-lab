## 🖥️ Virtual Machine Setup

This home SOC lab consists of three virtual machines. The Wazuh Server collects and analyzes security events from the Linux and Windows agents through a centralized monitoring platform.

### VM1 — Wazuh Server (Ubuntu Server)

**Purpose:** Hosts the Wazuh backend services and centralized security monitoring components.

| Component        | Configuration                                 |
| ---------------- | --------------------------------------------- |
| Operating System | Ubuntu Server 24.04 LTS                       |
| RAM              | **4 GB minimum**                              |
| Storage          | **80 GB minimum**                             |
| CPU              | 2 vCPUs recommended                           |
| Network          | Static IPv4 address                           |
| Services         | Wazuh Manager, Wazuh Indexer, Wazuh Dashboard |

**Important:** Allocate at least 4 GB of RAM and 80 GB of virtual disk storage to the Wazuh Server. The Indexer stores and processes security event data, so disk usage can increase as logs accumulate. Insufficient storage may cause indexing failures, service interruptions, or installation issues.

> **Recommendation:** Use a dynamically allocated 80 GB virtual disk if your virtualization software supports it. The virtual disk can grow as data is added, but the host computer must still have sufficient free physical storage.

### VM2 — Linux Agent (Ubuntu Desktop)

**Purpose:** Acts as a Linux endpoint monitored by the Wazuh Server.

| Component        | Configuration                    |
| ---------------- | -------------------------------- |
| Operating System | Ubuntu Desktop 24.04 LTS         |
| RAM              | 2–4 GB                           |
| Storage          | 25–40 GB                         |
| CPU              | 2 vCPUs                          |
| Network          | Same network as the Wazuh Server |
| Software         | Wazuh Agent                      |

**Monitoring objectives:**

* Monitor authentication and system logs.
* Detect suspicious login attempts.
* Monitor file integrity changes.
* Generate security events and investigate Wazuh alerts.

### VM3 — Windows Agent (Windows 10)

**Purpose:** Acts as a Windows endpoint for security event collection and analysis.

| Component        | Configuration                    |
| ---------------- | -------------------------------- |
| Operating System | Windows 10                       |
| RAM              | 2–4 GB                           |
| Storage          | 40–60 GB                         |
| CPU              | 2 vCPUs                          |
| Network          | Same network as the Wazuh Server |
| Software         | Wazuh Agent                      |

**Monitoring objectives:**

* Collect Windows security events.
* Monitor successful and failed login attempts.
* Investigate suspicious activity.
* Generate and analyze alerts in the Wazuh Dashboard.

Use a legitimate Windows installation or evaluation image for your lab. Windows 10 standard support ended on October 14, 2025, so keep the VM isolated or appropriately secured and consider a supported Windows version for longer-term use.

### 📊 Lab Architecture Overview

| VM  | Role                | Operating System         | Minimum RAM | Storage           |
| --- | ------------------- | ------------------------ | ----------- | ----------------- |
| VM1 | Central SIEM server | Ubuntu Server 24.04 LTS  | **4 GB**    | **80 GB minimum** |
| VM2 | Linux endpoint      | Ubuntu Desktop 24.04 LTS | 2 GB        | 25–40 GB          |
| VM3 | Windows endpoint    | Windows 10               | 2 GB        | 40–60 GB          |

**Note:** The agent specifications are starting points, not guarantees of optimal performance. Actual resource requirements depend on event volume, enabled services, and the applications running inside each VM.
