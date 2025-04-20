# 🧊 Azure Blob Storage

---

## 📦 What is Blob Storage?

Azure Blob Storage is used to store **unstructured data** like images, videos, documents, backups, and logs.

It’s designed for:
- High availability
- Scalability
- Secure object storage

Blob stands for **Binary Large Object**.

---

## 🧱 Types of Blobs

| Blob Type        | Description                                                                 |
|------------------|-----------------------------------------------------------------------------|
| **Block Blob**   | Stores text and binary data. Optimized for upload and storage of large files. |
| **Append Blob**  | Optimized for append operations like logging. Data is only appended.        |
| **Page Blob**    | Used for frequent read/write operations. Mainly for **Azure VMs (OS + Data disks)**. |

---

## 🗂️ Access Tiers (for Block Blobs)

Azure Blob Storage supports **four access tiers** based on how often data is accessed:

| Tier         | Description                                                                 | Minimum Storage Duration | Use Case                                 |
|--------------|-----------------------------------------------------------------------------|---------------------------|------------------------------------------|
| **Hot**      | Highest storage cost, lowest access cost. Optimized for frequent access.    | ❌ No minimum             | Active websites, real-time apps          |
| **Cool**     | Lower storage cost, higher access cost. Optimized for infrequent access.    | ✅ 30 days                 | Backup data, short-term archives         |
| **Cold**     | Lower cost than Cool, higher access cost. For rarely accessed data.         | ✅ 90 days                 | Long-term backups, rarely accessed files |
| **Archive**  | Lowest storage cost, very high latency and access cost. Offline storage.    | ✅ 180 days                | Legal data, compliance, long-term storage |

> 🔹 You can **change tiers anytime**, but if you delete/move data **before the minimum duration**, you will still be **charged for the full period**.

> ❗ **Archive** tier blobs must be **rehydrated** before access, which can take several hours.

---

## 🔒 Access Levels (Container Level)

Access levels define how the blobs inside a container can be accessed.

| Access Level        | Description                                                              |
|---------------------|--------------------------------------------------------------------------|
| **Private**         | Default. Only the account owner can access.                              |
| **Blob**            | Public can read blobs, but not list the container.                       |
| **Container**       | Public can read all blobs and list the container content.                |

> 🔹 Use **Private** for secure data.  
> 🔹 Use **Blob** or **Container** for public read-only data (e.g., website assets).

---

## 🔑 Access Keys

Each Storage Account has two access keys:
- Acts like **root credentials**
- Full access to everything in the account

> ❗ Avoid using Access Keys in code. Use SAS or RBAC instead.

---

## 🔐 Shared Access Signature (SAS)

SAS provides **limited access** to resources without sharing keys.

You can control:
- Resource type (blob, file, etc.)
- Permissions (read, write, delete)
- Expiry time
- IP address and protocol restrictions

### 🔸 Types of SAS:
- **User Delegation SAS** – Tied to Azure AD identity
- **Account SAS** – Access at account level
- **Service SAS** – Access to specific service like Blob, File, etc.

> ✅ SAS is preferred over access keys for fine-grained control.

---

## 🛡️ Immutable Blob Storage

Immutable blob storage allows you to **store data in a write-once, read-many (WORM)** state.

### 🔹 Use Cases:
- Regulatory compliance
- Financial/legal records

### 🔹 Policies:
- **Time-based retention** – Blob cannot be modified/deleted for a specific period.
- **Legal hold** – Blob is locked until explicitly cleared.

> ❗ Once a retention policy is locked, it **cannot be changed**.

---

## 📘 Exam Notes

- Know when to use **Block**, **Append**, or **Page** blobs.
- Understand **access levels** and implications of using public containers.
- Always prefer **SAS** over access keys for limited scope access.
- Use **access tiers** wisely to optimize **cost vs performance**.
- **Immutable storage** is important for **compliance and retention** needs.
- Be aware of the new **Cold tier** and how it fits between Cool and Archive.
- Know the **minimum storage duration** for Cool (30d), Cold (90d), and Archive (180d).

---
