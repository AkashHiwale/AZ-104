# 🌐 IP Addressing in Azure

---

## 📌 What is an IP Address?

- An **IP address** is a unique identifier assigned to a device or resource on a network.
- It allows resources to **communicate** over the internet or within private networks.
- Azure resources (like VMs, Load Balancers, Application Gateways) often require IP addresses.

---

## 🧱 Types of IP Addresses in Azure

| Type                     | Description |
|---------------------------|-------------|
| **Public IP Address**     | - Accessible over the internet.<br> - Used for communication outside the Azure network. |
| **Private IP Address**    | - Used within a Virtual Network (VNet).<br> - Not accessible from the internet. |
| **Dynamic IP Address**    | - Assigned when the resource starts.<br> - IP can change after a stop/start cycle. |
| **Static IP Address**     | - Manually assigned.<br> - Remains the same even after resource restarts. |

---

## 🔥 Public vs Private IP

| Public IP                  | Private IP               |
|-----------------------------|---------------------------|
| Exposed to the internet     | Stays inside the Azure VNet |
| Useful for web apps, APIs   | Useful for internal apps   |
| Requires extra security    | More secure by default     |

---

## 🛠️ How to Assign IP Addresses

- **Public IPs**: Attach to VMs, Load Balancers, Application Gateways.
- **Private IPs**: Assigned automatically when connecting a NIC to a subnet inside a VNet.

---

## ✨ Example: Creating a Public IP using Azure CLI

```bash
az network public-ip create --resource-group rg-demo --name myPublicIP --sku Standard
```

## 🧠 IP Allocation Methods

| Method  | Details |
|---------|---------|
| **Dynamic** | - IP assigned automatically at runtime.<br>- Most common for internal apps. |
| **Static**  | - IP reserved permanently.<br>- Important for DNS configurations, critical apps. |

---

## 📋 Important Points for Exam

- Standard SKU Public IPs are **zone-redundant** and **secure by default**.
- Private IP addresses are usually **assigned automatically** inside a VNet.
- You must choose **Static IP** if you need an IP that won't change after restart.
- **Dynamic IPs** are cheaper but less predictable.
- IP addresses are bound to **Regions** — you can't move a Public IP across regions directly.

---

## 🔍 Good to Know

- **Private IP range** follows RFC1918:
  - 10.x.x.x
  - 172.16.x.x to 172.31.x.x
  - 192.168.x.x

- **Public IPs** can have DNS labels (like `myapp.eastus.cloudapp.azure.com`).

- **IP SKU matters**:
  - **Basic SKU**: Older, less secure.
  - **Standard SKU**: Recommended, secure by default, supports availability zones.
