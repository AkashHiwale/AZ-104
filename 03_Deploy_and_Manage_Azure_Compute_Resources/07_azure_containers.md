# 📦 Azure Containers

---

## ✅ What is a Container?

A **container** is a lightweight, standalone, and executable package of software that includes:

- **Application code**
- **Dependencies**
- **Libraries**
- **Configuration files**
- A **lightweight OS layer**

This ensures the application runs consistently across different environments.

---

## 🧱 Key Characteristics

- Containers are **isolated** from each other.
- They share the **host operating system’s kernel**, unlike virtual machines.
- Faster to start and use **less resources** than full VMs.

---

## 💡 Why Containers?

- **Portability**: Consistent behavior across development, test, and production environments.
- **Efficiency**: Quick start-up and lower overhead.
- **Isolation**: Avoids conflicts between applications running on the same host.

---

## 🛠️ Underlying Components

Each container includes:
- A **lightweight OS** (like Alpine Linux or Ubuntu base image)
- The **application**
- Required **libraries**
- App **configuration files**

---

## ☁️ Container Services in Azure (Important for AZ-104)

Here are the main Azure services to run and manage containers:

| Azure Service              | Description                                                                 |
|----------------------------|-----------------------------------------------------------------------------|
| **Azure Container Instances (ACI)** | Fast and easy way to run containers without managing servers              |
| **Azure Kubernetes Service (AKS)**   | Full container orchestration using Kubernetes; scalable and production-ready |
| **App Service for Containers**      | Run containerized web apps on a fully managed platform                     |
| **Azure Container Registry (ACR)**  | Private Docker registry for storing and managing container images          |

---