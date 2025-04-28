
# 🛡️ Network Security Groups (NSG) in Azure

---

## 📌 What is a Network Security Group (NSG)?

- A **Network Security Group (NSG)** is a security filter that controls **inbound** and **outbound** network traffic at the **subnet** or **network interface** (NIC) level.
- NSGs use **rules** to allow or deny network traffic based on **source/destination IP**, **port**, and **protocol**.

---

## 🧱 Key Components of an NSG

| Component             | Description |
|------------------------|-------------|
| **Security Rules**     | - Define what traffic is allowed or denied. |
| **Priority**           | - Each rule has a priority (lower number = higher priority). |
| **Inbound Rules**      | - Control traffic coming **into** the resource. |
| **Outbound Rules**     | - Control traffic going **out** of the resource. |
| **Default Rules**      | - Azure provides built-in rules that can't be deleted but can be overridden. |

---

## 🔥 Where Can You Associate an NSG?

| Resource            | Notes |
|---------------------|-------|
| **Subnet**          | - Controls traffic for all resources within the subnet. |
| **Network Interface (NIC)** | - Controls traffic for a specific VM or resource. |

⚡ **Important**: If an NSG is applied at both NIC and Subnet, both NSGs are evaluated, and **DENY wins**.

---

## 🛠️ Example: Creating an NSG and Rules via Azure CLI

### Step 1: Create an NSG

```bash
az network nsg create --resource-group myResourceGroup --name myNSG
```

### Step 2: Create a Security Rule

```bash
az network nsg rule create \
  --resource-group myResourceGroup \
  --nsg-name myNSG \
  --name allow-ssh \
  --priority 1000 \
  --direction Inbound \
  --access Allow \
  --protocol Tcp \
  --source-address-prefixes '*' \
  --destination-port-ranges 22 \
  --destination-address-prefixes '*'
```

---

## ✨ How NSG Rules are Processed

- NSG evaluates rules based on **priority order**.
- **First matching rule wins** — processing stops once a rule matches.
- Default rules exist to:
  - Allow VNet inbound/outbound traffic.
  - Allow Azure Load Balancer inbound.
  - Deny all traffic by default if no rule matches.

---

## 🧠 Common Use Cases of NSG

| Scenario                     | Description |
|-------------------------------|-------------|
| **Allow SSH/RDP access**      | - Allow TCP 22 (SSH) or TCP 3389 (RDP) from specific IPs. |
| **Restrict internal traffic** | - Allow only specific subnets or VMs to talk to each other. |
| **Block internet access**     | - Deny outbound internet access for a subnet. |
| **Limit access to specific apps** | - Allow only required ports like HTTP (80), HTTPS (443) to web servers. |

---

## 📋 Important Points for Exam

- NSG rules are **stateful** — if you allow inbound traffic, the reply is automatically allowed.
- **Lower priority number = higher priority** (e.g., 100 is evaluated before 200).
- NSGs can be **associated** with **subnets** and/or **NICs**.
- Always **least privilege principle** — only allow what is needed.
- If NSG is not explicitly applied to a subnet or NIC, **no filtering occurs**.

---

## 🔍 Good to Know

- **Application Security Groups (ASG)**: Simplify managing security by grouping VMs logically instead of IP addresses.
- **Service Tags**: Use predefined tags like `Internet`, `VirtualNetwork`, `AzureLoadBalancer` in NSG rules to simplify configurations.
- **Flow Logs**: Enable NSG flow logs to capture network traffic information for monitoring or troubleshooting.

---

