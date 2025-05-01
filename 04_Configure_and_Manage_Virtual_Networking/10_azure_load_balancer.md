# ⚖️ Azure Load Balancer

---

## 📌 What is Azure Load Balancer?

- Azure Load Balancer is a **Layer 4 (Transport Layer)** load balancer.
- It distributes **inbound network traffic** across multiple virtual machines or services.
- Supports both **public** and **internal** traffic balancing.
- Provides **high availability**, **scalability**, and **redundancy** for your applications.

---

## 🧱 Types of Azure Load Balancer

| Type             | Description |
|------------------|-------------|
| **Public Load Balancer** | Distributes traffic from the internet to Azure VMs. |
| **Internal Load Balancer** | Distributes traffic inside a Virtual Network (VNet) or connected VNets. |
| **Gateway Load Balancer** | Integrates with 3rd-party network virtual appliances (NVAs). |

---

## 🔁 Load Balancing Rules

- Define how traffic is distributed.
- Match **front-end IP** to a **backend pool** using:
  - **Protocol (TCP/UDP)**
  - **Port**
  - **Health probe**

---

## 📦 Backend Pool

- A group of VM NICs or backend services that will receive the traffic.

---

## 🧪 Health Probes

- Periodically check the health of backend instances.
- If a backend instance fails a probe, it is **removed** from rotation.

````json
{
  "protocol": "Tcp",
  "port": 80,
  "intervalInSeconds": 15,
  "numberOfProbes": 2
}
````

---

## 🛠️ Example: Create Public Load Balancer using Azure CLI

````bash
az network lb create \
  --resource-group rg-demo \
  --name myLoadBalancer \
  --sku Standard \
  --frontend-ip-name myFrontEnd \
  --backend-pool-name myBackEndPool \
  --public-ip-address myPublicIP
````

---

## ⚙️ Key Components

| Component        | Description |
|------------------|-------------|
| **Frontend IP**  | Public or internal IP exposed to users. |
| **Backend Pool** | List of target NICs/VMs. |
| **Load Balancing Rule** | How to forward traffic from frontend to backend. |
| **Health Probe** | Defines how to monitor the health of backend endpoints. |
| **Inbound NAT Rules** | Allow port forwarding to individual VMs. |

---

## 📋 Important Points for Exam

- **Standard SKU** supports **zone redundancy** and **VNet integration**.
- **Basic SKU** is legacy and **not recommended** for production.
- Load Balancer is **region-specific**.
- Health probes are essential for **high availability**.
- **Inbound NAT rules** allow SSH or RDP into individual VMs through the Load Balancer.

---

## 🔍 Good to Know

- **Stateless** by default (uses 5-tuple hash).
- Works well with **Availability Sets** and **Virtual Machine Scale Sets**.
- **Does not support SSL termination** — use **Application Gateway** if needed.

