# 🌐 Azure Application Gateway

---

## 📌 What is Azure Application Gateway?

- Azure Application Gateway is a **Layer 7 (Application Layer)** load balancer.
- It enables you to manage **HTTP/HTTPS traffic** to your web applications.
- It can make **routing decisions based on URL, path, host headers, etc.**
- Supports features like **SSL termination**, **Web Application Firewall (WAF)**, and **session affinity**.

---

## 🧱 Key Features

| Feature | Description |
|--------|-------------|
| **URL-based Routing** | Direct requests to backend pools based on URL path or domain. |
| **Multi-site Hosting** | Host multiple websites behind a single Application Gateway. |
| **SSL Termination** | Decrypt HTTPS traffic at the gateway level to reduce VM load. |
| **WAF Integration** | Protects apps from OWASP top 10 vulnerabilities. |
| **Custom Probes** | Allows checking specific paths or ports on backends. |
| **Autoscaling** | Automatically adjust gateway instances based on traffic. |

---

## ⚙️ Components of Application Gateway

| Component           | Description |
|---------------------|-------------|
| **Frontend IP**      | IP exposed to users (public or private). |
| **Listener**         | Captures traffic from a specific port and protocol. |
| **Rules**            | Define how to route traffic (basic/path-based). |
| **Backend Pool**     | Target servers (VMs, App Services, etc.). |
| **HTTP Settings**    | Control port, protocol, cookies, and probes for backend. |
| **Health Probes**    | Check if backend services are healthy before routing traffic. |

---

## 🔐 Web Application Firewall (WAF)

- An optional SKU that provides centralized protection for web apps.
- Protects against:
  - SQL injection
  - Cross-site scripting (XSS)
  - OWASP Top 10
- Modes:
  - **Detection Mode**: Logs threats but does not block.
  - **Prevention Mode**: Blocks malicious traffic.

---

## 🛠️ Example: Create Application Gateway using Azure CLI

````bash
az network application-gateway create \
  --name myAppGateway \
  --location eastus \
  --resource-group rg-demo \
  --capacity 2 \
  --sku WAF_v2 \
  --frontend-port 80 \
  --http-settings-cookie-based-affinity Enabled \
  --vnet-name myVNet \
  --subnet mySubnet
````

---

## 🧠 Use Cases

- Hosting multiple web apps with different domain names.
- Secure access with SSL termination.
- Application-layer routing with custom logic.
- Protect web apps with integrated WAF.

---

## 📋 Important Points for Exam

- Works at **Layer 7** (vs. Load Balancer which works at Layer 4).
- **WAF is only supported on WAF and WAF_v2 SKUs**.
- Supports autoscaling and zone redundancy in v2 SKU.
- Can route to Azure App Services, VMs, and on-premise servers via VPN/ExpressRoute.

---

## 🔍 Good to Know

- Application Gateway can work with **Private Link** and **App Gateway for Containers**.
- Not suitable for low-latency TCP/UDP-based workloads — use **Azure Load Balancer** instead.
- Logs can be collected via **Azure Monitor** or **Log Analytics**.

