# 🔗 Virtual Network Integration (VNet Integration)

---

## 📌 What is VNet Integration?

- **Virtual Network Integration** allows an **Azure App Service** (Web App, Function App, etc.) to securely access **resources inside an Azure Virtual Network (VNet)**.
- It is used when the app needs to connect to **databases, APIs, or VMs** that are secured within a VNet.
- This feature only provides **outbound access from the app** to the VNet.

---

## 🧱 Key Characteristics

| Feature                      | Details |
|------------------------------|---------|
| **Outbound Access**          | Enables your app to reach private endpoints or resources inside the VNet. |
| **No Inbound Access**        | Does **not** allow inbound traffic **from** the VNet to the app. |
| **Subnet Required**          | A dedicated subnet is needed for integration. |
| **Regional Limitation**      | The app and VNet must be in the **same region** (for basic integration). |
| **Premium Plan Required**    | Required for **VNet integration** with private DNS or newer networking features. |

---

## 🛠️ How to Configure VNet Integration

````bash
az webapp vnet-integration add \
  --name myWebApp \
  --resource-group rg-demo \
  --vnet myVnet \
  --subnet mySubnet
````

---

## 🔄 Types of VNet Integration

| Type                | Description |
|---------------------|-------------|
| **Regional VNet Integration** | - Works when the app and VNet are in the **same region**.<br>- Supports access to private endpoints and resources. |
| **Gateway-required VNet Integration** | - Works across **regions**.<br>- Requires a **VPN Gateway** in the VNet.<br>- Deprecated for many scenarios in favor of regional integration. |

---

## 🔒 Use Cases

- Accessing **private databases** hosted in VNet (e.g., Azure SQL, PostgreSQL).
- Connecting to **custom APIs** hosted in VMs or internal Load Balancers.
- Enabling **private DNS resolution** from within the app.

---

## 📋 Important Points for Exam

- VNet Integration is **for outbound traffic only** from the App Service.
- **PremiumV2 or higher** App Service plans are required for advanced networking options.
- The integrated subnet **must not** have a Network Security Group (NSG) or Route Table that blocks traffic.
- Integration is **not required** to access public resources or services.

---

## 🔍 Good to Know

- You can view integration status using the **Azure Portal**, **Azure CLI**, or **PowerShell**.
- Private endpoints + VNet Integration allows full isolation of app traffic.
- Combine with **Private DNS Zones** to resolve internal hostnames.

