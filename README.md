# 🛡️Wazuh Home SOC Lab
![wazuh-banner](/screenshots/image.png)

A hands-on cybersecurity project focused on siem development, security monitoring, log analysis, alert investigation.

## 🏗️ Lab Architecture

The lab consists of three virtual machines connected through a bridged network. Ubuntu Server hosts the Wazuh components, while Ubuntu Desktop and Windows 11 act as monitored endpoints.

```text
                   HOME SOC LAB
                        |
              +---------+---------+
              |                   |
       Ubuntu Desktop          Windows 11
        Wazuh Agent            Wazuh Agent
              |                   |
              +---------+---------+
                        |
                 Bridged Network
                        |
                  Ubuntu Server
                        |
                    Wazuh SIEM
                        |
           +------------+------------+
           |            |            |
        Manager       Indexer     Dashboard
```

### Virtual Machine Setup

| VM  | Operating System | Role                                 | Network Configuration |
| --- | ---------------- | ------------------------------------ | --------------------- |
| VM1 | Ubuntu Server    | Wazuh Manager, Indexer and Dashboard | Bridged; static IPv4  |
| VM2 | Ubuntu Desktop   | Linux monitoring endpoint            | Bridged               |
| VM3 | Windows 11       | Windows monitoring endpoint          | Bridged               |

### Network Configuration

All three virtual machines use **bridged networking**, allowing them to connect to the same network.

* **Ubuntu Server (VM1):** Configured with a static IPv4 address so the endpoints can consistently reach the Wazuh Manager.
* **Ubuntu Desktop (VM2):** Connected to the bridged network as the Linux monitoring endpoint.
* **Windows 11 (VM3):** Connected to the bridged network as the Windows monitoring endpoint.

The Linux and Windows agents communicate with the Wazuh Manager using its configured IP address.

**Important network ports:**

| Port | Protocol       | Purpose                                    |
| ---- | -------------- | ------------------------------------------ |
| 1514 | TCP by default | Agent communication with the Wazuh Manager |
| 1515 | TCP            | Agent enrollment                           |
| 443  | TCP            | Wazuh Dashboard web access                 |

These are the default ports commonly used in this setup. Confirm the actual configuration on your server if you have changed any ports.

### Lab Components

| Component            | Purpose                                                        |
| -------------------- | -------------------------------------------------------------- |
| Wazuh Manager        | Receives and analyzes endpoint security data                   |
| Wazuh Indexer        | Stores and indexes security data                               |
| Wazuh Dashboard      | Provides the interface for monitoring and investigating events |
| Ubuntu Desktop Agent | Sends Linux endpoint data to the Wazuh Manager                 |
| Windows 11 Agent     | Sends Windows endpoint data to the Wazuh Manager               |

*The Manager, Indexer and Dashboard run on the same Ubuntu Server VM in this lab.*
