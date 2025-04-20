# 🧪 Azure Storage Features: Object Replication, Blob Snapshot & Blob Versioning

---

## 🔁 Object Replication

Object replication enables **automatic replication** of block blobs from one storage account (source) to another (destination) in the **same or different region**.

### ✅ Key Points:
- Only supports **block blobs**
- Works across **General-purpose v2** storage accounts
- Can replicate within the same region or across regions
- **Destination is read-only**
- Useful for:
  - Data backup
  - Disaster recovery
  - Compliance

### 🔐 Requirements:
- Both storage accounts must be in the **same Azure AD tenant**
- **Versioning must be enabled** on both source and destination
- Lifecycle rules can be set independently on destination blobs

---

## 📸 Blob Snapshots

A snapshot is a **read-only, point-in-time copy** of a blob.

### ✅ Key Points:
- Used for **backup or rollback**
- Each snapshot includes the blob's data + metadata at that time
- You can **create, list, restore, or delete** snapshots
- Stored in the same storage account and billed for **delta size** (only changes from original blob)

### 📦 Use Cases:
- Backup before application updates
- Recovery from accidental overwrite

---

## 🧬 Blob Versioning

Blob versioning automatically **maintains previous versions** of a blob whenever it's modified or deleted.

### ✅ Key Points:
- Keeps **immutable versions** of blobs
- Each update creates a new version
- Old versions can be:
  - **Accessed**
  - **Restored**
  - **Deleted manually**
- Helps protect data against:
  - Accidental deletion
  - Overwrites
  - Ransomware attacks

### 💡 Tips:
- Can be used with **lifecycle management** to delete older versions after a set time
- Supports **block blobs** only

---

## 📘 Exam Tip Summary:

| Feature           | Purpose                         | Key Benefit                              |
|------------------|----------------------------------|------------------------------------------|
| Object Replication | Cross-region blob copy          | Disaster recovery & compliance            |
| Blob Snapshot     | Point-in-time copy               | Quick backup & restore                    |
| Blob Versioning   | Track changes over time          | Data protection from accidental changes   |
