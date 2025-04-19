# 🚀 Azure Container Services

---

## 🧱 Azure Container Registry (ACR)

- A **private registry** to store and manage Docker container images.
- Fully managed by Azure.
- Can be integrated with ACI, AKS, and ACA.
- Works like Docker Hub but in your own Azure subscription.

### 🔐 Features:
- Azure AD authentication
- Image versioning and retention policies
- Geo-replication (Premium tier)

---

## 📦 Azure Container Instances (ACI)

- Run **containerized apps quickly** without managing any infrastructure.
- Supports both Linux and Windows containers.
- Billed per second — good for temporary or burst workloads.

### ✅ Use Cases:
- Testing and development
- Scheduled jobs or batch processing
- Event-driven apps

---

## ⚙️ Azure Container Apps (ACA)

- A **serverless container platform** for running **microservices, APIs, and background jobs**.
- Built on Kubernetes, Dapr, and Envoy (but you don’t need to manage any of that).
- Supports **auto-scaling**, including scale to zero.

### ✅ Use Cases:
- APIs and background services
- Event-driven apps
- Microservices needing versioning or revisions

---

## 🔍 Difference Between ACR, ACI, and ACA

| Feature/Service       | ACR (Registry)                                  | ACI (Instances)                                 | ACA (Apps)                                                |
|-----------------------|--------------------------------------------------|--------------------------------------------------|------------------------------------------------------------|
| Purpose               | Store container images                          | Run containers on-demand                        | Run serverless container-based apps                        |
| Infra management      | Fully managed registry                          | No infra management needed                      | No infra management, built on Kubernetes                   |
| Scaling               | N/A                                              | Manual (fixed size or per job)                  | Autoscaling, including scale to zero                       |
| Costing               | Based on storage tier                           | Pay per second of container runtime             | Pay for active resources only                             |
| Networking            | VNet integration available                      | Public/private IPs                              | Built-in HTTP ingress, VNet integration supported          |
| Best for              | Container storage for AKS/ACI/ACA               | Simple or short-running containers              | APIs, microservices, and background tasks with auto-scaling |
| Integration           | Used with ACI, AKS, ACA                         | Can pull images from ACR                        | Can pull images from ACR                                   |

---

## 🧠 Exam Tip

- **ACR** is not used to run containers, only to **store** them.
- **ACI** is best for **quick, lightweight, temporary containers**.
- **ACA** is ideal for **scalable microservices** without needing to learn Kubernetes.

---
