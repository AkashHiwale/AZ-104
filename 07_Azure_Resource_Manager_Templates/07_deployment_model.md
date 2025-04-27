# 🧑‍💻 ARM Template - Deployment Models: Complete and Incremental

---

## 📌 What are Deployment Models in ARM Templates?

In ARM templates, deployment models define how changes to resources are applied during deployment. There are two primary deployment models available for deploying ARM templates: **Complete** and **Incremental**.

Each model affects how existing resources are handled and determines how Azure will deploy new or updated resources.

---

## 🛠️ Complete Deployment Model

### 📌 What is Complete Deployment?

- In a **Complete** deployment, **Azure will delete any resources** that are not defined in the new template.
- It’s ideal for creating a **fresh deployment** or ensuring that resources that are no longer needed are completely removed.
- This model ensures that the state of the environment matches the template exactly after deployment.
  
> **Use case**: Use the Complete deployment model when you want to remove resources that no longer exist in the updated template or when creating a completely new environment.

### 🧱 Example of Complete Deployment

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "resources": [
    {
      "type": "Microsoft.Resources/resourceGroups",
      "apiVersion": "2019-05-10",
      "location": "EastUS",
      "name": "rg-demo"
    },
    {
      "type": "Microsoft.Storage/storageAccounts",
      "apiVersion": "2019-06-01",
      "name": "storagedemo123",
      "location": "EastUS",
      "sku": {
        "name": "Standard_LRS"
      },
      "kind": "StorageV2"
    }
  ]
}
```

- When this template is deployed with the **Complete** deployment model, **any resources not defined** (such as any other storage accounts or resource groups that were previously deployed) will be **deleted**.

---

## 🧱 How Complete Deployment Works

1. **Resource Deletion**:
   - Any resources present in the resource group but not defined in the template will be deleted.
   - This is useful for cleaning up unused resources.

2. **Ideal for Fresh Start**:
   - When setting up new environments or staging environments where you don’t need to keep the previous state.

3. **Overwriting Existing Resources**:
   - Any existing resources defined in the template will be **updated** or **recreated** if their properties differ from the new template.

---

## 🛠️ Incremental Deployment Model

### 📌 What is Incremental Deployment?

- In an **Incremental** deployment, only the resources **defined or modified** in the new template will be deployed, while **existing resources** that are not referenced in the template remain unchanged.
- This model allows you to add, update, or remove specific resources without affecting the entire environment.

> **Use case**: Use the Incremental deployment model when you want to **add or modify specific resources** without deleting or modifying the entire infrastructure.

### 🧱 Example of Incremental Deployment

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "resources": [
    {
      "type": "Microsoft.Storage/storageAccounts",
      "apiVersion": "2019-06-01",
      "name": "storagedemo123",
      "location": "EastUS",
      "sku": {
        "name": "Standard_LRS"
      },
      "kind": "StorageV2"
    }
  ]
}
```

- When this template is deployed with the **Incremental** model, only the **defined resources** (in this case, the storage account) will be modified or created. Any other existing resources (e.g., resource groups or other storage accounts) **will not be affected**.


### 🧱 Deployment Command

- Complete mode is triggered when you specify it in the deployment command (CLI or PowerShell):

    ``` bash
    az deployment group create --resource-group myResourceGroup --template-file template.json --mode Complete
    ```
    >In this case, any unlisted resources (e.g., storagedemo456) in the resource group would be deleted.

- Incremental mode is the default behavior if no mode is specified:

    ``` bash
    az deployment group create --resource-group myResourceGroup --template-file template.json --mode Incremental
    ```

    >In this case, only resources defined in the template (like storagedemo123) would be created or updated.

---

## 🧱 How Incremental Deployment Works

1. **Resource Addition**:
   - New resources defined in the template will be **added** to the environment if they do not already exist.

2. **Resource Update**:
   - If a resource is already present and defined in the template with new properties, **only the properties** will be updated (the resource itself is not recreated).

3. **No Resource Deletion**:
   - Resources that are not referenced in the new template will **not be deleted**. This helps in scenarios where you want to add or modify specific resources without impacting others.

---

## 🧠 Key Differences Between Complete and Incremental Models

| Feature                     | Complete Deployment                               | Incremental Deployment                           |
|-----------------------------|--------------------------------------------------|--------------------------------------------------|
| **Resource Deletion**        | Resources not defined in the template are deleted | Resources not in the template are not affected   |
| **Use Case**                 | Clean start, environment refresh                | Add or update resources without affecting others |
| **Ideal For**                | Fresh environments or resetting existing setups  | Updating specific resources in a live environment |
| **Impact on Existing Resources** | Resources are recreated or updated | Resources are updated only if specified          |

---

## 🧠 Exam Tips

- Understand when to use **Complete** vs **Incremental** deployment models.
- Know the effect of each model on resource deletion and updates.
- Recognize that the **Complete** deployment model is destructive, while **Incremental** is safer for updating or adding resources without affecting the entire environment.

