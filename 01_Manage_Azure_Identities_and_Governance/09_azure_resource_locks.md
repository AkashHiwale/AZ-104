
# 🔒 Azure Resource Locks

---

## 📌 What Are Resource Locks?

Azure Resource Locks help you **prevent accidental deletion or modification** of your resources.

They are particularly useful for protecting critical infrastructure in your environment.

---

## 🔐 Types of Locks

1. **Read-only (`CanNotDelete`)**:
   - Users can **read** and **list** resources.
   - **Modifications and deletions are blocked**.
   - It’s similar to assigning a **Reader** role but enforced at the **management level**.

2. **Delete (`ReadOnly`)**:
   - Allows reading and modifying resources.
   - **Prevents deletion** of the resource.

---

## 📍 Where Can You Apply Locks?

- **Subscription level**
- **Resource Group level**
- **Individual Resource level**

> 🔄 Locks are **inherited** by child resources.  
> For example, if you apply a lock at the Resource Group level, all resources inside it inherit the lock.

---

## 🛠️ How to Apply Locks

### Azure Portal
- Go to the resource or resource group.
- Select **Locks** under **Settings**.
- Click **Add**, choose the lock type, and give a name.

### Azure CLI
```bash
az lock create   --name "LockName"   --lock-type CanNotDelete   --resource-group "MyResourceGroup"
```

### PowerShell
```powershell
New-AzResourceLock -LockName "LockName" `
  -LockLevel CanNotDelete `
  -ResourceGroupName "MyResourceGroup"
```

---

## 🚫 Limitations and Notes

- Locks can be **overridden** by users with **Owner** or **User Access Administrator** roles.
- Locks do **not apply** to billing or policy assignments.
- They help **enforce governance** but are not a substitute for RBAC.

---

## 🧠 Exam Tips

- Know the difference between **Delete** and **Read-only** locks.
- Understand that **locks are inherited** by all child resources.
- Be familiar with how to create locks using **Portal**, **CLI**, and **PowerShell**.
- Understand that **RBAC and locks serve different purposes**—RBAC manages access, locks enforce protection at the management level.
