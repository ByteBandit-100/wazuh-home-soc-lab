## 🌐 Network Configuration

Ensure that all virtual machines are connected to the same network so they can communicate with each other.

### Network Requirements

* **Wazuh Server (Ubuntu Server):** Hosts the Wazuh Manager, Wazuh Indexer, and Wazuh Dashboard.
* **Linux Agent (Ubuntu Desktop):** Sends security events and logs to the Wazuh Server.
* **Windows Agent (Windows 11):** Sends Windows security events and logs to the Wazuh Server.

### Network Setup

1. Configure all virtual machines to use the same network or a compatible bridged network configuration.
2. Assign a **static IPv4 address** to the Wazuh Server to prevent its IP address from changing after a reboot.
3. Configure the Linux and Windows agents to communicate with the Wazuh Server using its static IP address.
4. Verify connectivity between the virtual machines before configuring the Wazuh agents.

### Connectivity Verification

Run the following command on the Linux and Windows agent machines, replacing `<WAZUH_SERVER_IP>` with your Wazuh Server's actual IP address.

**Linux:**

```bash
ping <WAZUH_SERVER_IP>
```

**Windows (PowerShell or Command Prompt):**

```powershell
ping <WAZUH_SERVER_IP>
```

**Note:** Bridged networking is one option, but it is not mandatory. A shared virtual network can also work if it allows communication between all three VMs. Ensure that the Wazuh Server's static IP address does not conflict with another device on the network.
