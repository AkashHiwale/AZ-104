
# 🌐 Azure Subnets

---

## 📌 What is a Subnet?

- A **Subnet** is a smaller network segment inside a **Virtual Network (VNet)**.
- Subnets help **organize and isolate** Azure resources.
- Each subnet has its own **IP address range** within the VNet's address space.
- They enable applying **security controls**, **route policies**, and **resource grouping**.

---

## 🧱 Why Use Subnets?

| Reason                  | Description |
|--------------------------|-------------|
| **Segmentation**         | - Separate resources (e.g., databases, web servers) for better management and security. |
| **Security**             | - Apply Network Security Groups (NSGs) at subnet level. |
| **Control Traffic Flow** | - Use Route Tables to manage network traffic between subnets. |
| **Scalability**          | - Plan IP addressing efficiently for future growth. |

---

## 🛠️ Subnet Properties

| Property         | Details |
|------------------|---------|
| **Name**         | - Unique within a VNet. |
| **Address Range**| - CIDR block that falls within VNet's address space (e.g., 10.0.1.0/24). |
| **Network Security Group (NSG)** | - Optional security filter at subnet level. |
| **Route Table**  | - Custom routing rules can be associated. |
| **Service Endpoints** | - Extend Azure services into your VNet securely. |
| **Delegations**  | - Assign a subnet to specific Azure services (e.g., Azure SQL). |

---

## 🖼️ Subnet Architecture Diagram

Here is an example how subnets are organized inside a VNet:

![Azure Subnet Architecture](https://github.com/AkashHiwale/AZ-104-Azure-Administrator-Exam-Study-Notes/raw/feature/configure-and-manage-virtual-networking/04_Configure_and_Manage_Virtual_Networking/images/subnet.JPG)

---

## ✨ Example: Create a Subnet using Azure CLI

```bash
az network vnet subnet create \
  --address-prefix 10.0.1.0/24 \
  --name mySubnet \
  --resource-group myResourceGroup \
  --vnet-name myVNet
```

---

## 🔥 Important Rules for Subnets

- Subnet's address prefix must be **inside** the VNet address space.
- Subnets **cannot overlap** in address range within a VNet.
- Once created, you **cannot change** the subnet address range without deleting and recreating.
- Resources within a subnet can **communicate freely** unless restricted using NSGs or route tables.
- A subnet can span **Availability Zones**, but not multiple Regions.

---

## 🔗 Special Concepts Related to Subnets

| Concept                 | Description |
|--------------------------|-------------|
| **Service Endpoints**    | - Allow secure access to Azure services over the VNet. |
| **Private Endpoints**    | - Access Azure PaaS services privately via a private IP. |
| **Delegated Subnets**    | - Reserve a subnet for specific Azure services like Azure App Service Environment. |
| **Gateway Subnet**       | - Special subnet to deploy VPN or ExpressRoute gateways. Needs specific name `GatewaySubnet`. |

---

## 📋 Important Points for Exam

- **Address space planning** is critical before creating VNets and subnets.
- **GatewaySubnet** must exist for deploying VPN Gateway; no NSG recommended on it.
- **NSGs** and **Route Tables** can be associated with a subnet (or even individual NICs).
- **Service Endpoints** improve security by allowing private access to Azure services.
- Subnets **must not overlap** with each other within the same VNet.

---

## 🔍 Good to Know

- Azure reserves **five IP addresses** per subnet:
  - First IP: Network address
  - Last IP: Broadcast address
  - Three more for Azure internal usage
- Always leave enough IPs in subnets for scaling (especially when planning with VM Scale Sets or AKS).

