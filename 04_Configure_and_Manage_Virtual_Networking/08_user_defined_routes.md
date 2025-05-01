
# 🛣️ Azure User Defined Routes (UDRs)

---

## 📌 What are User Defined Routes?

- **User Defined Routes (UDRs)** allow you to **control traffic flow** within an Azure virtual network (VNet).
- By default, Azure handles routing automatically — UDRs let you override this default behavior for **custom routing** needs.

---

## 🧱 Why Use UDRs?

| Use Case                                  | Description |
|--------------------------------------------|-------------|
| **Force traffic to Network Virtual Appliance (NVA)** | Use UDRs to route all traffic through a firewall or other inspection device. |
| **Custom next hop**                        | Direct traffic to a specific device or gateway. |
| **Split traffic**                          | Send internet-bound traffic one way, private traffic another. |
| **Override default routing**               | Customize default behavior set by Azure system routes. |

---

## 🧭 Types of Next Hop in UDR

| Next Hop Type             | Description |
|---------------------------|-------------|
| **Virtual Appliance**      | IP address of a firewall or NVA. |
| **Virtual Network**        | Default system routing within the VNet. |
| **Internet**               | Sends traffic directly to the internet. |
| **Virtual Network Gateway** | Routes traffic to on-prem through VPN/ExpressRoute. |
| **None**                   | Blocks traffic intentionally. |

---

## 🛠️ Example: Creating a UDR using Azure CLI

```bash
az network route-table create \
  --name myRouteTable \
  --resource-group rg-demo \
  --location eastus

az network route-table route create \
  --resource-group rg-demo \
  --route-table-name myRouteTable \
  --name route-to-nva \
  --address-prefix 10.0.0.0/16 \
  --next-hop-type VirtualAppliance \
  --next-hop-ip-address 10.1.1.4
```

> 📎 Associate the route table with a **subnet** to make the custom routes take effect.

---

## 🔗 Associating UDR with a Subnet

```bash
az network vnet subnet update \
  --vnet-name myVnet \
  --name mySubnet \
  --resource-group rg-demo \
  --route-table myRouteTable
```

---

## ⚙️ Important Behaviors

- UDRs **override system routes** for specified address prefixes.
- UDRs are evaluated **before** NSGs — so even routed traffic must be allowed by NSG.
- You can have **multiple custom routes** in a route table.

---

## 📋 Exam Tips

- UDRs are used for **customizing traffic flow**, especially for NVAs.
- Know how to associate UDRs with subnets.
- Understand different **next hop types** and when to use them.
- UDRs **don't apply globally** — they apply to specific subnets.

---

## 🔍 Good to Know

- You can’t apply more than one route table per subnet.
- **System routes** are always present, but UDRs can override them.
- Use **Network Watcher** to verify route tables and troubleshoot traffic.

