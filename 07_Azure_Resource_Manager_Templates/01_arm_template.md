# 📄 Azure Resource Manager (ARM) Templates

---

## 📌 What are ARM Templates?

- **ARM templates** are **JSON** files used to **automate the deployment** of Azure resources.
- Define the **infrastructure as code** (IaC).
- Enable **consistent, repeatable deployments**.
- Deployed through **Azure Resource Manager** (the management layer for Azure).

---

## 🛠️ Key Components

- **Schema**: Defines the version of the template.
- **Parameters**: Values you pass during deployment (e.g., location, VM size).
- **Variables**: Simplify templates by storing reusable values.
- **Resources**: Define the Azure resources to deploy (VMs, storage accounts, etc.).
- **Outputs**: Return values after deployment (like resource IDs).

---

## 📚 Example ARM Template Structure

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "parameters": {
    "storageAccountName": {
      "type": "string"
    }
  },
  "variables": {},
  "resources": [
    {
      "type": "Microsoft.Storage/storageAccounts",
      "apiVersion": "2022-09-01",
      "name": "[parameters('storageAccountName')]",
      "location": "[resourceGroup().location]",
      "sku": {
        "name": "Standard_LRS"
      },
      "kind": "StorageV2",
      "properties": {}
    }
  ],
  "outputs": {}
}
```

---

## 🚀 Deployment Methods

- Azure Portal
- Azure CLI  
  ```bash
  az deployment group create --resource-group <rg-name> --template-file <template-file.json>
  ```
- Azure PowerShell  
  ```powershell
  New-AzResourceGroupDeployment -ResourceGroupName <rg-name> -TemplateFile <template-file.json>
  ```
- ARM REST API
- Azure DevOps / GitHub Actions pipelines

---

## 🧑‍🎓 Benefits

- **Automation**: Eliminate manual deployments.
- **Consistency**: Same template → same resources → fewer errors.
- **Version control**: Templates can be stored in GitHub or Azure Repos.
- **Modular**: Can use linked templates for complex deployments.

---

## 🔥 Exam Tips

- Understand the structure: **Parameters**, **Variables**, **Resources**, **Outputs**.
- Know how to **deploy using CLI and PowerShell**.
- Know that ARM templates are **declarative** (you state what you want; Azure figures out how to get there).
- Understand **error handling**: If one resource fails to deploy, the whole deployment can fail (depending on the mode).
- Deployment Modes:
  - **Incremental**: Adds or updates resources (default).
  - **Complete**: Deletes resources not specified in the template.
