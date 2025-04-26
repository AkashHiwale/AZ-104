# 📊 Azure Monitor

Azure Monitor is a **comprehensive monitoring service** in Azure that collects, analyzes, and acts on telemetry data from your Azure and on-premises environments.

---

## 🌐 What Does It Monitor?

- **Applications** (via Application Insights)
- **Infrastructure** (Azure VMs, AKS, Networking)
- **Azure resources** (via Azure Resource Metrics)
- **Custom sources** (via diagnostics settings, agents, APIs)

---

## 🧩 Components

### 🔹 Metrics
- Numerical values describing performance.
- Collected at regular intervals.
- Stored in a time-series database.
- Example: CPU usage, disk IOPS.

### 🔹 Logs
- Structured records of events.
- Collected using the **Log Analytics agent**.
- Stored in **Log Analytics Workspace**.
- Example: Activity logs, diagnostics logs.

---

## 🛠 Tools and Features

- **Azure Monitor Metrics**: Visualize resource performance with charts.
- **Log Analytics**: Query log data using Kusto Query Language (KQL).
- **Alerts**
  - Alerts notify you when a condition is met on metrics or logs.
  - Types of alerts:
    - **Metric alerts**: Triggered on performance metrics.
    - **Log alerts**: Based on custom log queries.
    - **Activity log alerts**: Based on subscription-level events.
    - **Prometheus alerts**: For AKS and container workloads.
  - **Actions**: Trigger emails, webhooks, Azure Functions, Logic Apps, or runbooks.
  - **Action groups**: Define a set of actions to execute when an alert fires.

### 🔕 Alert Suppression
- **Alert suppression** avoids alert fatigue by preventing repeat alerts.
- You can set a **"suppression period"** when creating an alert rule.
- During the suppression window, no new alerts are fired even if the condition persists.
- Useful for flapping conditions or known temporary issues.

- **Example**: If CPU > 80% for 5 minutes → Alert fires → Suppression set to 30 minutes → No further alerts during this window even if CPU remains high.

- Helps reduce **noise** and focuses attention on **critical issues**.

- **Smart detection** in Application Insights can also auto-suppress non-critical alerts.

---

## 📊 Dashboards

- Create custom dashboards to visualize:
  - Metrics
  - Log queries
  - Alerts
- Can be shared with teams for unified views.

---

## 🧠 Exam Tips

- Know the difference between **metrics** and **logs**.
- Understand **Log Analytics**, **KQL basics**, and how to create **log alerts**.
- **Application Insights** is part of Azure Monitor for app-level monitoring.
- Remember how **action groups** and **suppression** work in alerting.
