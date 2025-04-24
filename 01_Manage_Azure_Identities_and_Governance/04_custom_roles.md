# 🛠️ Azure Custom Roles

Custom roles in Azure allow you to define your own **set of permissions** when **built-in roles don’t meet your needs**.

---

## 📌 What is a Custom Role?

- A **user-defined role** that specifies the exact permissions (actions) needed.
- Based on the **least privilege principle** — only allow what is necessary.
- Managed using **JSON** definitions.

---

## 🔧 Custom Role Structure

A custom role includes:

- **Name** – Friendly name of the role.
- **Actions** – What the role can do (e.g., read, write).
- **NotActions** – What the role cannot do.
- **DataActions / NotDataActions** – Used for **data-level access** (like reading blobs).
- **AssignableScopes** – Where the role can be assigned (subscription/resource group scope).

---

## 🧪 Example JSON

```json
{
  "Name": "Custom Reader Role",
  "IsCustom": true,
  "Description": "Can read everything except secrets",
  "Actions": [
    "Microsoft.Resources/subscriptions/resourceGroups/read",
    "Microsoft.Compute/virtualMachines/read"
  ],
  "NotActions": [
    "Microsoft.KeyVault/vaults/secrets/read"
  ],
  "AssignableScopes": [
    "/subscriptions/<subscription-id>"
  ]
}
```

---

## 🧠 Exam Tips

- Custom roles are **defined in JSON** and can be created using:
  - Azure CLI (`az role definition create`)
  - PowerShell
  - ARM Templates
- Use **NotActions** and **NotDataActions** to fine-tune permissions.
- **AssignableScopes** determines where the role is visible and assignable.
- Custom roles cannot grant more permissions than the user creating them has.
- Custom roles are useful when:
  - Built-in roles are **too broad**.
  - You need **precise control** over actions.

---

## 🔄 Custom Roles vs Built-in Roles

| Feature           | Built-in Role | Custom Role |
|------------------|---------------|-------------|
| Predefined       | ✅ Yes         | ❌ No        |
| Editable         | ❌ No          | ✅ Yes       |
| Uses JSON        | ❌ No          | ✅ Yes       |
| Granular Control | ⚠️ Limited     | ✅ Full       |

---
