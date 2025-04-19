# 📦 Azure Storage Account

---

## ✅ What is a Storage Account?

An Azure Storage Account is a service that gives access to **durable and highly available storage** in the cloud.  
It allows you to store **blobs, files, queues, tables, and disks**.

---

## 📁 Types of Storage Services in a Storage Account

| Service         | Description                                      |
|-----------------|--------------------------------------------------|
| **Blob Storage**   | For storing unstructured data (images, videos, backups, etc.) |
| **File Storage**   | Fully managed file shares (SMB protocol)        |
| **Queue Storage**  | For messaging between application components    |
| **Table Storage**  | NoSQL key-value store for structured data       |
| **Disk Storage**   | For attaching virtual disks to VMs              |

---

## 🏷️ Storage Account Types

| Type                   | Description                                                                 |
|------------------------|-----------------------------------------------------------------------------|
| **General-purpose v2** | Recommended. Supports all storage types with latest features and pricing.   |
| **General-purpose v1** | Older version. Limited features and more expensive in many cases.           |
| **Blob Storage**       | Optimized for storing large amounts of unstructured object data (only blobs). |

> 🔹 Use **General-purpose v2** for most workloads unless you have a specific reason not to.

---

## 💾 Performance Tiers

| Tier         | Description                                           |
|--------------|-------------------------------------------------------|
| **Standard** | Backed by HDD. Cost-effective, used for general storage needs. |
| **Premium**  | Backed by SSD. Higher performance, used for IO-intensive apps. |

---

## 🌍 Replication Options

| Type                     | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| **LRS (Locally Redundant Storage)**      | Replicates data 3 times within a single data center                        |
| **ZRS (Zone-Redundant Storage)**         | Replicates data across 3 availability zones in a region                    |
| **GRS (Geo-Redundant Storage)**          | Replicates data to a secondary region (LRS in both primary and secondary) |
| **GZRS (Geo-zone Redundant Storage)**    | Combines ZRS in primary + GRS to secondary region                         |

> 🔹 GRS and GZRS provide **disaster recovery** capabilities.

---

## 🧠 Exam Tips

- Know **when to choose** LRS vs GRS vs ZRS based on durability and cost.
- Use **General-purpose v2** unless asked specifically.
- For high performance (e.g., databases), choose **Premium**.
- Understand use cases for **Blob, File, Queue, Table**, and **Disk** services.

---

## 📘 Summary Table

| Feature              | General Purpose v2 | Blob Storage | File Storage | Premium |
|----------------------|--------------------|--------------|--------------|---------|
| Blob Support         | ✅                 | ✅           | ❌           | ✅      |
| File/Queue/Table     | ✅                 | ❌           | ✅           | ❌      |
| SSD (High Perf.)     | Optional           | ❌           | ❌           | ✅      |
| Replication Options  | LRS, ZRS, GRS, GZRS| LRS, GRS     | LRS, GRS     | LRS     |

---
