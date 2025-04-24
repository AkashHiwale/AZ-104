# 🛂 Azure RBAC Conditions

RBAC Conditions allow **more fine-grained control** over resource access by adding **conditional logic** to role assignments.

---

## 🎯 What are RBAC Conditions?

- An **extension to Azure RBAC** that lets you define **when** and **how** a user can perform certain actions.
- Useful for **limiting access without creating custom roles**.
- Available **only with Azure AD Premium P1 or P2**.

---

## 🧱 Structure of a Condition

RBAC Conditions are expressed in a **logical condition expression**, applied on top of a role assignment.

> Example:  
> Allow access **only if** the resource is in a specific region or has a specific tag.

---

## 🧪 Example Use Cases

| Use Case | Description |
|----------|-------------|
| Tag-based access | Allow access only to resources with a specific tag |
| Resource name filters | Grant access only to resources with specific naming patterns |
| Location-based | Allow actions only in a specific region (e.g., `East US`) |

---

## 🧠 Exam Tips

- RBAC Conditions provide **extra control** without creating **custom roles**.
- You **must use Azure CLI, PowerShell, or ARM templates** to create conditions (not supported in the Portal).
- Remember: Conditions are part of **role assignment**, not role definition.
- Requires **Microsoft Entra ID P1/P2** (formerly Azure AD Premium).

---

## 🧬 Example Condition (Tag-based)

```bash
az role assignment create \
  --assignee <userPrincipalName> \
  --role "Reader" \
  --scope "/subscriptions/<subId>/resourceGroups/<rgName>" \
  --condition "@Resource[Microsoft.Resources/subscriptions/resourceGroups:tags.Environment] StringEquals 'Test'" \
  --condition-version "2.0"
