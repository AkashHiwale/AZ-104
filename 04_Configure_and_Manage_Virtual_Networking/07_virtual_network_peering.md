
# 🔗 Azure Virtual Network Peering

---

## 📌 What is Virtual Network Peering?

- **Virtual Network Peering (VNet Peering)** connects two virtual networks (VNets) in Azure, allowing resources in both VNets to communicate with each other using **private IP addresses**.
- Peered VNets appear as one for connectivity purposes, even across **regions** (global peering).

---

## 🧱 Key Characteristics

| Feature                         | Description |
|----------------------------------|-------------|
| **Private Communication**        | Traffic between VNets uses Azure's backbone — no public internet involved. |
| **Low Latency, High Bandwidth** | Ideal for workloads needing fast inter-network communication. |
| **Cross-Region Supported**      | Enables Global VNet Peering across different Azure regions. |
| **Non-Transitive**              | Peering is not transitive — VNet A ↔ VNet B, VNet B ↔ VNet C does not mean A ↔ C. |

---

## 🛠️ Types of Peering

| Type               | Description |
|--------------------|-------------|
| **Intra-region**   | Peering between VNets in the same Azure region. |
| **Global Peering** | Peering between VNets in different regions. |

---

## 🧠 Key Concepts

- **Bidirectional Configuration**: Peering must be configured on both VNets.
- **Name Resolution**: DNS configuration is needed for cross-VNet name resolution.
- **VNet Address Spaces** must not overlap.
- **Peering Link**: Created in each VNet, defining traffic direction and permissions.

---

## 🖼️ Virtual Network Peering Architecture Diagram

Here is an example how Peering is configured:

![Azure Peering Architecture](https://github.com/AkashHiwale/AZ-104-Azure-Administrator-Exam-Study-Notes/raw/feature/configure-and-manage-virtual-networking/04_Configure_and_Manage_Virtual_Networking/images/Peering.JPG)

---

## ✨ Example: Create Peering using Azure CLI

```bash
az network vnet peering create \
  --name LinkVNetAtoB \
  --resource-group RG1 \
  --vnet-name VNetA \
  --remote-vnet VNetB_ID \
  --allow-vnet-access
```

> 🔁 You must also run the same command in reverse for **VNetB → VNetA**.

---

## 🔒 Access Control Options in Peering

| Option                  | Purpose |
|--------------------------|---------|
| **allow-vnet-access**     | Allows traffic between VNets. |
| **allow-forwarded-traffic** | Accepts traffic forwarded by a network virtual appliance. |
| **allow-gateway-transit** | Allows use of a shared VPN Gateway. |
| **use-remote-gateways**   | Allows a peered VNet to use the remote VNet's gateway. |

---

## 📋 Exam Tips

- Peering allows **private communication** across VNets without internet exposure.
- **Peering is not transitive** — requires explicit connections between all VNets.
- **Address space must not overlap** for peering to work.
- Understand the meaning of **allow-vnet-access**, **gateway transit**, and **forwarded traffic**.

---

## 🔍 Good to Know

- **Global peering** supports VNets in different subscriptions.
- **Network Security Groups (NSGs)** still apply — communication is not automatic unless NSGs allow it.
- Can be monitored through **Network Watcher** and flow logs.

---

