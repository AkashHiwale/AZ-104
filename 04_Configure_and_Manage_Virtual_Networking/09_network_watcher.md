# 🛠️ Azure Network Watcher

---

## 📌 What is Network Watcher?

- **Azure Network Watcher** is a **monitoring and diagnostic service** for Azure virtual networks.
- It helps you analyze, diagnose, and troubleshoot networking issues in your Azure environment.

---

## 🧱 Key Capabilities of Network Watcher

| Feature                  | Description |
|--------------------------|-------------|
| **Topology**             | Visualizes resources and relationships within a virtual network. |
| **Connection Troubleshoot** | Checks if a VM can reach a destination (IP/port) and returns latency & hop data. |
| **IP Flow Verify**       | Validates whether traffic is allowed/denied based on NSG rules. |
| **NSG Flow Logs**        | Captures logs for traffic allowed/denied by NSGs. |
| **Packet Capture**       | Captures packets from a VM for deep inspection. |
| **Next Hop**             | Identifies the next hop for traffic from a VM to a destination. |
| **Effective Security Rules** | Shows the effective NSG rules applied to a network interface. |
| **VPN Troubleshoot**     | Diagnoses VPN connectivity issues. |

---

## ✨ Example: Enabling Network Watcher using Azure CLI

````bash
az network watcher configure --resource-group rg-demo --locations eastus --enabled true
````

---

## 🔎 Example: Run IP Flow Verify

````bash
az network watcher verify-ip-flow \
  --resource-group rg-demo \
  --direction Inbound \
  --protocol TCP \
  --local 10.0.0.4 \
  --remote 192.168.1.1 \
  --local-port 80 \
  --remote-port 1000 \
  --nic nic-id
````

---

## 🧠 When to Use Each Tool

| Tool                      | Use Case |
|---------------------------|----------|
| **Connection Troubleshoot** | Test VM connectivity to a destination IP and port. |
| **IP Flow Verify**         | Debug NSG-related traffic blocks. |
| **Next Hop**               | Check where traffic is routed from a VM. |
| **Packet Capture**         | Capture and analyze traffic from a VM. |
| **Effective Rules**        | Understand real NSG rules affecting a NIC. |

---

## 📋 Important Points for Exam

- Network Watcher is **region-specific**. You must enable it in each region where diagnostics are needed.
- **Packet Capture** requires the Microsoft Monitoring Agent to be installed on the VM.
- **NSG Flow Logs** are stored in a **Storage Account** and can be analyzed using **Log Analytics**.
- Helps with **both proactive monitoring and reactive troubleshooting**.
- Essential for understanding **real-time traffic behavior** and **NSG enforcement**.

---

## 🔍 Good to Know

- Integration with **Azure Monitor** and **Log Analytics** makes logs queryable.
- You can automate diagnostics with **Logic Apps** or **Azure Functions** based on Watcher outputs.
- **No extra cost** for enabling Network Watcher — you're billed for diagnostics run or logs stored.

