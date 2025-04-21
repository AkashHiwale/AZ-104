# 🗂️ Azure Management Groups

Azure Management Groups help you manage **access, policies, and compliance** across multiple Azure subscriptions in a unified way.

---

## 🎯 Purpose

- Organize **multiple subscriptions** into a hierarchy for governance.
- Apply **Azure Policy, RBAC, and Blueprints** at a management group level.
- Ensure consistent configuration and standards across environments.

---

## 🧱 Key Features

- Supports a **hierarchical structure** of up to six levels deep (excluding root).
- Every directory has a **single root management group**.
- Subscriptions **inherit policies and RBAC** from their parent management group.

---

## 📁 Structure

```
Root Management Group
├── Management Group A
│   ├── Subscription 1
│   └── Subscription 2
└── Management Group B
    └── Subscription 3
```

---

## 🔐 Access Management

- RBAC roles assigned at a management group level are inherited by all **child management groups** and **subscriptions**.
- You can assign **owners, contributors, readers**, or **custom roles** at the top level for broad access.

---

## 📌 Use Cases

- Enforce governance policies across all subscriptions.
- Group subscriptions by department (e.g., HR, IT, Finance).
- Enable centralized billing and cost management.

---

## 🛠️ Management Tools

- Azure Portal (Management Groups blade)
- Azure CLI  
  ```bash
  az account management-group create --name <group-name> --display-name "MyGroup"
  ```
- PowerShell  
  ```powershell
  New-AzManagementGroup -GroupName <group-name> -DisplayName "MyGroup"
  ```

---

## 🧠 Exam Tips

- Remember that **management groups are evaluated before subscriptions** in the policy/RBAC hierarchy.
- **Inheritance of policies and access** is a key concept.
- Be aware of **default/root management group** and how to manage it.

