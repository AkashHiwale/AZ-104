# 🌐 Azure Web Apps (App Service)

---

## ✅ What is Azure Web Apps?

Azure Web Apps is a **fully managed Platform-as-a-Service (PaaS)** offering for hosting web applications, REST APIs, and mobile backends.

---

## 🧱 Key Features

- Supports multiple languages: **.NET, Java, Node.js, Python, PHP, Ruby**
- Built-in **load balancing** and **auto-scaling**
- Supports **Linux and Windows** based environments
- Integrated with **CI/CD** tools (GitHub, Azure DevOps, etc.)
- Custom domain and SSL support
- Built-in monitoring and diagnostics

---

## 🚀 Benefits

- **No need to manage infrastructure**
- Fast deployment and scaling
- Easy integration with other Azure services (Key Vault, ACR, Application Insights)

---

## ⚙️ App Service Plans

Defines the **pricing tier and features** for your Web App:

| Tier       | Description                                      |
|------------|--------------------------------------------------|
| **Free/Shared** | Dev/test workloads, limited features             |
| **Basic**       | Small production workloads                     |
| **Standard**    | Production workloads, scaling, daily backups   |
| **Premium**     | High performance, VNet integration, advanced scaling |
| **Isolated**    | Runs in your own VNet for high-security apps   |

---

## 🔐 Security Features

- Authentication & Authorization (App Service Authentication)
- Integration with Azure AD, Google, Facebook, etc.
- HTTPS only enforcement
- VNet integration (Premium and Isolated tiers)

---

## 📘 Exam Tip

- Azure Web Apps is ideal when you want to **host code without managing VMs**.
- Know the **App Service Plan tiers** and what they offer.
- **Scaling options**: manual, scheduled, or rule-based autoscaling.
- Web Apps can be deployed using **containers** as well.

---

## 📦 Related Services

- **App Service Environment (ASE)**: Dedicated and isolated environment for high-security and network isolation.
- **Deployment Slots**: Used for staging, testing, and seamless swap to production.

---

## 🧠 Quick Summary

| Feature               | Azure Web Apps                      |
|-----------------------|-------------------------------------|
| Type                  | PaaS                                |
| Supports Containers   | Yes                                 |
| Infra Management      | Handled by Azure                    |
| Auto-scaling          | Yes                                 |
| Use Cases             | Websites, APIs, mobile backends     |
| CI/CD                 | GitHub, DevOps, Bitbucket, etc.     |

---
