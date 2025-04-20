# 📂 Azure File Share

Azure File Share is a fully managed cloud file share that you can mount like a traditional file share using SMB or NFS protocols.

---

## 📌 Key Features

- Supports **SMB (Server Message Block)** and **NFS (Network File System)** protocols
- Can be mounted on **Windows, Linux, or macOS**
- Useful for **lift-and-shift** of on-prem file servers to the cloud
- Can be accessed **concurrently** by multiple VMs
- Can be integrated with **Azure File Sync** for hybrid storage setups

---

## 📦 Access Tier & Transactions

Azure File Share has specific **transaction behavior** depending on the tier being accessed or written to:

| **Tier**                        | **Transaction Optimized (Destination)**           | **Hot (Destination)**                   | **Cool (Destination)**                  |
|----------------------------------|--------------------------------------------------|-----------------------------------------|-----------------------------------------|
| **Transaction Optimized (Source)** | --                                               | 1 hot write transaction per file        | 1 cool write transaction per file       |
| **Hot (Source)**                 | 1 hot read transaction per file                  | --                                      | 1 cool write transaction per file       |
| **Cool (Source)**                | 1 cool read transaction per file                 | Data retrieval per total used GiB      | 1 cool read transaction per file        |

---

## 📸 Snapshots

- File share snapshots capture the **entire file share at a point in time**
- Used for **backup and restore**
- Snapshots are **incremental**, saving only changes
- You can **recover individual files** from a snapshot

---

## ♻️ Soft Delete

- Protects against **accidental deletion**
- When enabled, deleted shares can be **restored within a retention period** (up to 365 days)
- Applies to:
  - **File shares**
  - **Files and directories**

### ✅ Benefits:
- Prevents data loss due to user error
- Recovery is **self-service** via Azure Portal or CLI

---

## 📘 Summary

| Feature      | Purpose                          |
|--------------|----------------------------------|
| Access Tier  | Cost optimization based on usage |
| Snapshot     | Point-in-time backup & restore   |
| Soft Delete  | Recover deleted data easily      |
