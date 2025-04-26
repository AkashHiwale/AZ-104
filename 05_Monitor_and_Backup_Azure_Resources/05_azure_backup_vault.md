# 📦 Azure Backup Vault

---

## 📚 What is a Backup Vault?

- An **Azure Backup Vault** is a **storage entity** in Azure that holds backup data for different Azure resources.
- It manages and organizes backups for services like Azure VMs, SQL databases, file shares, and more.
- Helps **centralize backup management** and **monitor backup jobs**.

---

## 🔥 Key Features

- Centralized management for backups.
- Can store backups across **multiple resource types**.
- Supports **soft delete** to protect backups from accidental deletion.
- Integration with Azure Monitor for **alerting** on backup status.

---

## 🏷️ Types of Backup Vaults

| Vault Type             | Description |
| :--------------------- | :---------- |
| **Recovery Services Vault** | Used for older Azure Backup and Site Recovery scenarios. Still widely used for VM backups, SQL Server backups, etc. |
| **Backup Vault**           | A newer vault type designed specifically for modern Azure Backup workloads. Simpler and optimized for data backup. |

✅ **For AZ-104**, focus mainly on **Recovery Services Vault**.

---

## 🛠️ How to Create a Backup Vault

1. Go to **Azure Portal**.
2. Search for **Recovery Services Vault** or **Backup Vault**.
3. Click **Create**, choose Subscription, Resource Group, Region.
4. Set a name for the vault and review + create.

---

## 🧠 Important Concepts

- **Backup Policy**: Defines backup schedule and retention periods.
- **Soft Delete**:
  - Retains deleted backups for **14 days** (default) even after accidental deletion.
- **Geo-Redundancy**:
  - Backup Vaults use **GRS (Geo-Redundant Storage)** by default for high availability.

---

## 🛡️ Security

- Use **Azure Role-Based Access Control (RBAC)** to manage access to the vault.
- Enable **Soft Delete** and **Multi-User Authorization** for extra protection against deletion attacks.

---

## 🧠 Exam Tips

- **Soft Delete** protects backup data from accidental deletes.
- Know the **difference between Recovery Services Vault and Backup Vault**.
- Understand how **Backup Policies** and **Retention** are applied.
- Remember that **vaults are region-specific** — backups are tied to the region of the vault.

---
