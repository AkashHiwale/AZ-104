# 🔐 Azure Role-Based Access Control (RBAC)

RBAC allows you to **control who has access to Azure resources**, what they can do, and what areas they have access to.

---

## ✅ Key Concepts

| Term               | Description |
|--------------------|-------------|
| **Security Principal** | Object requesting access – user, group, service principal, or managed identity |
| **Role Definition**    | A collection of permissions (e.g., read, write, delete) |
| **Scope**              | The level at which access applies – **Management Group > Subscription > Resource Group > Resource** |
| **Role Assignment**    | Process of attaching a role to a security principal at a specific scope |

---

## 🧭 Scopes in Detail

RBAC can be applied at 4 levels:
1. **Management Group** – highest level, applies to multiple subscriptions
2. **Subscription** – applies to all resources within the subscription
3. **Resource Group** – applies to all resources in the group
4. **Resource** – most granular level

> **Note**: Role assignments are **inherited**. If you assign at the subscription level, it applies to all child resource groups and resources.

---

## 👤 Built-In Roles

| Role                  | Permissions |
|------------------------|-------------|
| **Owner**              | Full access, including managing access |
| **Contributor**        | Can manage everything except access |
| **Reader**             | Read-only access |
| **User Access Administrator** | Can manage RBAC permissions but not resource content |

There are also **resource-specific roles**, e.g., `Virtual Machine Contributor`, `Storage Blob Data Reader`.

---

## ⚒️ Custom Roles

- You can define your own roles using **JSON**.
- Use when **built-in roles don’t meet your requirements**.

```json
{
  "Name": "Custom Reader",
  "Actions": [ "Microsoft.Resources/subscriptions/resourceGroups/read" ],
  "NotActions": [],
  "AssignableScopes": ["/subscriptions/{subscriptionId}"]
}
```

---

## 🔄 Difference Between RBAC and IAM

- **RBAC**: Resource-level access control within Azure  
- **IAM (Identity & Access Management)**: Azure portal interface used to manage RBAC

---

## 🧠 Exam Tips

- Understand the difference between **Owner**, **Contributor**, and **Reader**
- Know that **role assignments are inherited** down the hierarchy
- **RBAC is for Azure Resource access**. For **application-level access**, consider **Entra ID roles**
- Use the **least privilege principle** – give users only the access they need
- Know how to assign a role using **Azure Portal**, **CLI**, and **PowerShell**

---

## 🧪 Bonus: CLI Example

```bash
az role assignment create \
  --assignee <userPrincipalName> \
  --role "Reader" \
  --scope /subscriptions/<subId>/resourceGroups/<rgName>
```
