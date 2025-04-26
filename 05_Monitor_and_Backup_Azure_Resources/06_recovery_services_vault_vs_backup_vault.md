# 🔥 Difference Between Recovery Services Vault and Backup Vault

---

| Feature                         | Recovery Services Vault                         | Backup Vault                              |
| :------------------------------ | :---------------------------------------------- | :---------------------------------------- |
| **Purpose**                     | Used for backup and disaster recovery scenarios (VMs, SQL DBs, Azure File Shares, Site Recovery) | Used for backup of newer workloads (Azure Database for PostgreSQL, Azure Blobs, Azure Disks, etc.) |
| **Supported Workloads**         | Azure VMs, SQL workloads, SAP HANA, Azure File Shares, Azure Site Recovery | Azure Blobs, Azure Disks, Azure Database for PostgreSQL (Flexible Server) |
| **Architecture**                | Older architecture but still heavily used and supported | Newer design optimized for modern workloads |
| **Soft Delete**                 | Supported (14 days retention for VMs) | Supported |
| **Granular RBAC**               | Basic RBAC support | Improved RBAC with Azure built-in roles |
| **Management**                  | Slightly complex for large-scale modern backup needs | Simplified and targeted for backup workloads only |
| **Usage in AZ-104 Exam**         | Very important (focus area) | Know basics (newer concept) |
| **Restore Options**             | Cross-region restore supported (for GRS vaults) | Restore within same region (for now) |
| **Geo-Redundancy**              | Available (GRS, LRS options) | Available |
| **Example Services**            | VM backup, SQL Server backup, SAP HANA backup, Site Recovery | Blob backup, Disk backup, PostgreSQL backup |

---

## 🧠 Exam Tips

- Focus more on **Recovery Services Vault** for traditional backup workloads (VMs, SQL).
- Understand that **Backup Vault** is optimized for **newer Azure services** and **future backup scenarios**.
- Both vaults support **Soft Delete** to protect against accidental deletion.
- Vaults are **region-specific** — backup and recovery happen in the same region unless using GRS.

---
