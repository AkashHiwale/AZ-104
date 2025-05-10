# 🧠 Azure Administrator – Essential Concepts

Welcome! Here’s a curated list of **high-value Azure insights** for managing resources efficiently—perfect for AZ-104 exam revision or real-world cloud administration. 🌐💼

---

## 📌 Key Points to Remember

### 🖧 Load Balancing & VM Configuration
1. 🧩 To attach a VM to a **Load Balancer**, it must be part of either an **Availability Set** or a **VM Scale Set**.
2. 🚫 VMs **cannot be added** to an Availability Set after creation—they must be assigned during deployment.
3. 🛑 To **resize a VM** within an Availability Set, **stop all VMs** in the set before performing the operation.

### 🔁 Resource Management & Movement
4. 🔒 When **moving resources** to another resource group:
   - If the **target group has a ReadOnly lock**, the move will **fail**.
   - If it has a **Delete lock**, the move is **allowed**.
5. 📍 A **Network Interface (NIC)** and its **Virtual Network (VNet)** must be in the **same Azure region**.
6. 🌐 For a **Standard Load Balancer**, all VMs must belong to the **same VNet**.

### 👥 Identity & Access
7. 👤 During **bulk user deletion**, only the **User Principal Name (UPN)** for each user is required.

### 🏷️ Tagging & Governance
8. 🏷️ **Resource tags** can be applied at the **subscription**, **resource group**, and **individual resource** levels.
9. 🚫 You **cannot assign a Basic SKU IP address** to a **Standard Load Balancer**.

### 🔐 Networking & Security
10. 🔧 The **Azure Bastion Subnet** must be at least **/26** in size.

### 🚚 Storage & Data Migration
11. 📦 For **data transfers > 30 TB**, use **Azure Data Box** for optimal performance.
12. 💎 **Premium file shares** are only supported in the **FileStorage** account type.

### 🧭 App Services & Networking
13. 🧵 You only need **one App Service Plan** if all Web Apps use the **same OS**.
14. 🔄 You **cannot move a VM** directly between Virtual Networks—you must **delete and recreate** it in the target VNet.

---

> ✨ *These tips reflect real-world challenges and best practices, tailored for both exam prep and production environments.*

---
📌 *Feel free to fork this repo, star it, or contribute your own Azure learnings!*
