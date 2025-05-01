
# 🔐 Azure Bastion

---

## 📌 What is Azure Bastion?

- **Azure Bastion** is a **PaaS (Platform-as-a-Service)** offering that provides **secure and seamless RDP/SSH connectivity** to Azure virtual machines **without exposing them to the public internet**.
- It allows you to **connect to VMs using the Azure Portal**, without requiring a public IP on the VM.

---

## 🧱 Key Features of Azure Bastion

| Feature                         | Description |
|----------------------------------|-------------|
| **No Public IP Required**        | - VMs do not need public IP addresses for remote access. |
| **Secure Browser-Based Access**  | - Connect to VMs via RDP/SSH using Azure Portal. |
| **Protection from Port Scanning**| - VMs are not exposed to the public internet, avoiding port scanning attacks. |
| **Fully Managed Service**        | - Azure handles scaling, availability, and maintenance. |

---

## 🔒 Security Benefits

- Helps **enforce zero-trust network access**.
- No need to open ports like **3389 (RDP)** or **22 (SSH)** in NSG.
- Communication between the Azure Bastion and VMs happens over the **private IP** within the VNet.

---

## 🖼️ Bastion Architecture Diagram

Here is an example how bastion is configured:

![Azure Bastion Architecture](https://github.com/AkashHiwale/AZ-104-Azure-Administrator-Exam-Study-Notes/raw/feature/configure-and-manage-virtual-networking/04_Configure_and_Manage_Virtual_Networking/images/Bastion.JPG)

---

## 🛠️ How to Deploy Azure Bastion

### Step 1: Create a Bastion Host

```bash
az network bastion create \
  --name myBastion \
  --resource-group myResourceGroup \
  --vnet-name myVNet \
  --public-ip-address myBastionIP \
  --location eastus
```

> ⚠️ Note: Bastion requires a **subnet named `AzureBastionSubnet`** with at least a **/27** address range.

### Step 2: Create the AzureBastionSubnet

```bash
az network vnet subnet create \
  --name AzureBastionSubnet \
  --resource-group myResourceGroup \
  --vnet-name myVNet \
  --address-prefix 10.0.1.0/27
```

---

## 🌐 Connection Experience

- Go to the VM in Azure Portal → Click **Connect** → Choose **Bastion** tab.
- Provide username/password or SSH key and start session.
- Everything runs inside the **browser**, no local RDP/SSH client needed.

---

## 🔍 Important Considerations

| Consideration          | Notes |
|------------------------|-------|
| **Cost**               | Bastion is billed hourly. Consider auto-shutdown policies if unused. |
| **Subnet Requirement** | Must create a dedicated subnet named `AzureBastionSubnet`. |
| **Public IP**          | Azure Bastion itself needs a public IP (VMs do not). |
| **Region**             | Azure Bastion must be deployed in the same region as the VNet. |
| **Peered VNets**       | Supports connections to peered VNets with some configuration. |

---

## 📋 Important Points for Exam

- **No Public IP** is required on VMs when using Azure Bastion.
- **AzureBastionSubnet** must exist in the VNet for Bastion deployment.
- Azure Bastion **provides secure, browser-based RDP/SSH** sessions.
- Helps reduce **attack surface** by eliminating need for open RDP/SSH ports.

---

## 💡 Good to Know

- Bastion is ideal for secure environments (e.g., production workloads).
- Can be combined with **Just-In-Time (JIT) VM access** for layered security.
- **No client software required** — works via browser over HTTPS (port 443).