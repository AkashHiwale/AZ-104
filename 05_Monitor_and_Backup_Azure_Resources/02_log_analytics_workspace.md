# 📘 Log Analytics Workspace

A **Log Analytics Workspace** is a central environment in Azure Monitor where log data is collected, stored, and analyzed.

---

## 🧱 What Is It?

- It's a **container** where data collected by Azure Monitor is stored.
- Used to run **Kusto Query Language (KQL)** queries on logs.
- Data can come from:
  - Azure resources (VMs, storage, network, etc.)
  - On-premises servers
  - Diagnostics settings
  - Azure Security Center
  - Application Insights

---

## 🧰 Key Features

- Collects **platform logs**, **metrics**, and **custom logs**.
- Supports **centralized log management** across subscriptions and regions.
- Can **query across multiple workspaces** (cross-workspace querying).
- Used by other services like:
  - **Azure Monitor**
  - **Microsoft Sentinel**
  - **Azure Automation**

---

## 🔐 Access Control

- Role-based access control (RBAC) can be applied at the workspace level.
- Also supports more granular control using **table-level access**.

---

## 📥 Data Sources

- Virtual Machines (via Azure Monitor Agent or Log Analytics Agent)
- Azure PaaS services (via Diagnostic settings)
- Custom applications (via REST API or SDKs)

---

## 🔍 Querying Logs

- Queries are written in **KQL (Kusto Query Language)**.
- You can filter, sort, and analyze log data.
- Example:
  ```kql
  Heartbeat
  | where TimeGenerated > ago(1h)
  | summarize Count = count() by Computer
  ```

---

## 💰 Pricing

- Charged based on:
  - Data **ingested** per GB
  - Data **retention** (first 31 days are free)
- You can set **retention period** (1 to 730 days).

---

## 🧠 Exam Tips

- Remember that Log Analytics Workspace is **required for Azure Monitor Logs**.
- Be familiar with **KQL basics**.
- Know how to **connect a resource** to a workspace via diagnostic settings.
- Understand **data retention**, ingestion costs, and workspace-based RBAC.
