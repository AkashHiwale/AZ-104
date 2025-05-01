# 🌐 Domain Name System (DNS) in Azure

---

## 📌 What is DNS?

- **DNS (Domain Name System)** translates **domain names** (e.g., `www.contoso.com`) into **IP addresses**.
- It's like a phonebook for the internet — instead of remembering IPs, users remember names.
- Azure provides DNS services for both **public** and **private** domains.

---

## 🧱 Types of DNS in Azure

| Type               | Description |
|--------------------|-------------|
| **Azure DNS (Public)** | Host your domain in Azure and manage DNS records like A, CNAME, MX. |
| **Azure Private DNS**  | Resolve names within a **virtual network (VNet)**. Useful for internal services. |

---

## 🧩 Azure DNS Key Concepts

| Term               | Description |
|--------------------|-------------|
| **Zone**           | A DNS zone represents a domain (e.g., `contoso.com`). |
| **Record Set**     | A collection of DNS records in a zone (e.g., A, AAAA, MX, CNAME). |
| **Name Resolution**| The process of mapping domain names to IP addresses. |

---

## 🛠️ Supported DNS Record Types

| Record Type | Description |
|-------------|-------------|
| **A**       | Maps a name to an IPv4 address. |
| **AAAA**    | Maps a name to an IPv6 address. |
| **CNAME**   | Maps a name to another name (alias). |
| **MX**      | Defines mail servers for the domain. |
| **NS**      | Delegates a DNS zone to use the given name servers. |
| **PTR**     | Reverse lookup: IP → Domain name. |
| **SRV**     | Defines location of servers for specific services. |
| **TXT**     | Stores arbitrary text — often used for verification (e.g., SPF, DKIM). |

---

## ✨ Example: Creating a DNS Zone and Record using Azure CLI

````bash
# Create a DNS Zone
az network dns zone create \
  --resource-group rg-demo \
  --name contoso.com

# Add an A Record
az network dns record-set a add-record \
  --resource-group rg-demo \
  --zone-name contoso.com \
  --record-set-name www \
  --ipv4-address 10.1.2.3
````

---

## 🔐 Private DNS Zones

- Allow name resolution **within one or more VNets**.
- Eliminate the need to maintain custom DNS servers.
- Supports **auto registration** for virtual machines using DHCP.

````bash
# Create a Private DNS zone
az network private-dns zone create \
  --resource-group rg-demo \
  --name contoso.local

# Link it to a VNet
az network private-dns link vnet create \
  --resource-group rg-demo \
  --zone-name contoso.local \
  --name link-vnet \
  --virtual-network myVnet \
  --registration-enabled true
````

---

## 🧠 Use Cases

- Hosting websites with custom domains.
- Internal service discovery using private DNS.
- Centralized DNS management across hybrid environments.
- Secure and scalable DNS for applications in Azure.

---

## 📋 Important Points for Exam

- **Azure DNS** is global and high availability is built-in.
- You must **delegate your domain** to Azure DNS name servers for public DNS to work.
- **Private DNS** supports **auto registration** of Azure VM hostnames.
- Azure DNS zones can be managed via **Azure CLI**, **PowerShell**, **Portal**, and **ARM templates**.

---

## 🔍 Good to Know

- Azure DNS does **not support domain registration** (e.g., buying `contoso.com`) — use third-party registrars for that.
- You can integrate Azure DNS with **Traffic Manager** for geo-routing and high availability.
- Use **Conditional Forwarding** in hybrid networks to resolve custom names from on-premises.

