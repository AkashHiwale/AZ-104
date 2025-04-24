# 🔄 Moving Azure Resources Across Resource Groups and Subscriptions

---

## 📌 What is Resource Move?

Azure allows you to **move resources**:
- Between **resource groups** within the same subscription
- Between **subscriptions** (same or different Azure AD tenants)

This is helpful for **reorganizing resources**, **cost allocation**, or **project migrations**.

---

## ✅ Supported Resources

- Most Azure resources can be moved.
- Some resources have **limitations** or **dependencies** (e.g., backup vaults, recovery services).
- Always check: [Azure Resource Move Support](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/move-support-resources)

---

## 🚀 How to Move Resources

### Azure Portal
1. Go to the **Resource Group** or the **Resource**.
2. Click **Move > Move to another resource group** or **Move to another subscription**.
3. Select destination RG or Subscription.
4. Validate and confirm.

### Azure CLI
```bash
az resource move \
  --destination-group <destination-rg> \
  --ids <resource-id1> <resource-id2>
```

### PowerShell
```powershell
Move-AzResource -DestinationResourceGroupName "<destination-rg>" `
                -ResourceId "<resource-id>"
```

---

## ⚠️ Important Considerations

- **Downtime**: Some services experience brief unavailability during the move.
- **Role Permissions**: You need **Microsoft.Resources/moveResources/action** permission on source and destination.
- **Locks**: Resources or RGs with **resource locks** cannot be moved.
- **Billing Implications**: Moving across subscriptions might affect billing and cost tracking.
- **Dependencies**: Some resources must be moved together (e.g., NIC with VM).
- **Marketplace**: Resources deployed from Marketplace may not be supported for move across subscriptions.

---

## ❌ Unsupported Scenarios

- Moving between subscriptions **in different tenants** may not be supported for all resources.
- Certain region-specific resources or legacy services may not be eligible.

---

## 🧠 Exam Tips

- Know which **permissions** are required for moving resources.
- Understand that **resource locks** prevent movement.
- Be familiar with **CLI and Portal steps** to move resources.
- Some resources have **dependencies** and **downtime risks**—check documentation before moving.
