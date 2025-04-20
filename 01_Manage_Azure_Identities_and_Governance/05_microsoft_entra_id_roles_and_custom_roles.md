# 👤 Microsoft Entra ID Roles & Custom Roles

Microsoft Entra ID (formerly Azure AD) provides **role-based access control** to manage **directory-level access** for users, groups, and apps.

---

## 🎯 Built-in Entra ID Roles

These are predefined roles with specific permissions to manage directory resources.

### 🔑 Common Roles

| Role                      | Description                                                |
|---------------------------|------------------------------------------------------------|
| **Global Administrator**  | Full access to all admin features. Can assign any role.    |
| **User Administrator**    | Manage users and groups, reset passwords.                  |
| **Groups Administrator**  | Create, update, delete groups and manage memberships.      |
| **Helpdesk Administrator**| Reset passwords and monitor service health.                |
| **Application Administrator** | Manage all applications and assign users.          |
| **Privileged Role Administrator** | Manage role assignments in Entra ID.            |

> 🧠 **Tip**: Only the **Global Administrator** can assign the **Privileged Role Administrator** role.

---

## ⚙️ Custom Roles in Entra ID

Create roles with specific permissions when built-in roles don’t fit your needs.

### 🧾 Key Points

- Permissions selected from a **directoryRolePermission** list.
- **Premium P1 or P2 license required.**
- Scope limited to the **tenant (directory-wide)**.

### ✅ Example Use Case

Create a custom role that:
- Can reset passwords for a specific group of users.
- Can read but not modify user profile data.

### 📌 How to Create

- Use **Microsoft Entra Admin Center**, PowerShell, or Microsoft Graph API.
- Define:
  - Role name
  - Description
  - Allowed permissions
  - Assignable scopes

---

## 🧠 Exam Tips

- Entra ID roles = **Directory-level** access.
- Azure RBAC roles = **Azure resource** access.
- Use **custom Entra roles** when:
  - You need fine-grained control over directory permissions.
  - Built-in roles don’t meet your security needs.
- You can assign roles to:
  - Users
  - Groups
  - Service principals

---

## 🔄 RBAC vs Entra ID Roles

| Feature              | Azure RBAC                    | Microsoft Entra ID Roles         |
|----------------------|-------------------------------|----------------------------------|
| Scope                | Resource, RG, Subscription     | Tenant / Directory-wide          |
| Purpose              | Azure resource access          | Directory & identity management  |
| Custom Role Support  | ✅ Yes                         | ✅ Yes (P1/P2 license needed)     |
