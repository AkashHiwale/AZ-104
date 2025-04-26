
# 🔄 Azure Backup

---

## 📌 What is Azure Backup?

- Azure Backup is a **cloud-based backup solution**.
- It helps protect data in Azure services like Virtual Machines, SQL databases, and on-premises servers.
- Provides **centralized management** and **monitoring**.

---

## 🛡️ Key Features

- **Application-consistent backups**: Ensures that applications are backed up in a consistent state.
- **Long-term retention**: Configure policies for both short-term and long-term backup retention.
- **Instant Restore**: Quickly restore files or VMs without waiting for full recovery.
- **Geo-redundancy**: Store backup data in different Azure regions (Geo-Redundant Storage - GRS).
- **Security**: Soft delete, encryption at rest, multi-user authorization (MUA).

---

## 🏢 Components

- **Recovery Services Vault**: Logical container to manage backup data and policies.
- **Backup Policies**: Define backup schedule and retention period.

---

## 🔄 Supported Workloads

- Azure Virtual Machines (Windows/Linux)
- SQL Server on Azure VMs
- Azure Files and Azure Blob Storage (preview)
- **On-premises machines** using:
  - **MARS Agent (Microsoft Azure Recovery Services Agent)**
  - **Azure Backup Server (MABS)**
  - **System Center Data Protection Manager (DPM)**

---

## 🛠️ MARS Agent

- The **MARS Agent** is used to back up:
  - Files and folders
  - System state
- Directly backs up data **from on-premises servers or Azure VMs** to Azure Recovery Services Vault.
- **No need for additional infrastructure** (like a backup server).
- Ideal for **small to medium environments**.

---

## 🛠️ How Backup Works

1. **Create** a Recovery Services Vault.
2. **Define** a backup policy (frequency + retention).
3. **Install** MARS Agent for file-level backups (for on-premises).
4. **Enable Backup** on resources.
5. **Data is backed up** to Azure according to the policy.

---

## 🚨 Soft Delete Feature

- Protects backup data even after accidental deletion of the VM or backup item.
- Data remains in **soft delete state for 14 additional days**.

---

## 📦 Storage Redundancy Options

- **Locally Redundant Storage (LRS)**: Replicates data within a single region.
- **Geo-Redundant Storage (GRS)**: Replicates data to a secondary Azure region for disaster recovery.

---

## 🧠 Exam Tips

- **Recovery Services Vault** is mandatory to configure backup.
- **Soft Delete** is enabled by default for Azure VMs.
- Know the **difference between GRS and LRS** storage options.
- **Azure Backup vs Azure Site Recovery**: Backup is for data protection; Site Recovery is for disaster recovery (failover).
- Backup policies automate **daily/weekly backup schedules**.
- **MARS Agent** is used mainly for file-level backups of on-premises machines.

