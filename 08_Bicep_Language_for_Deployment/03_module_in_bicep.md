# 🧑‍💻 Modules in Bicep

---

## 📌 What are Modules in Bicep?

- **Modules** in Bicep allow you to break down large templates into **smaller, reusable** components.
- They promote **separation of concerns**, **better organization**, and **reuse** across deployments.
- Each module is just another Bicep file that you can call from your main Bicep file.

---

## 🛠️ How Modules Work

- You create a separate Bicep file (`.bicep`) for a resource or a group of resources.
- In your main template, you call the module using the `module` keyword.
- You can pass **parameters** to modules and control their **scope**.

> Use a `module` block to call a reusable Bicep file.

Example structure:

```bicep
module <moduleName> '<path-to-bicep-file>.bicep' = {
  name: '<deploymentName>'
  params: {
    <parameterName>: <value>
  }
}
```

---

## 🧱 Example 1: Basic Module Usage

Suppose you have a `storage.bicep` file that defines a Storage Account:

```bicep
// storage.bicep
param storageAccountName string
param location string = 'EastUS'

resource storage 'Microsoft.Storage/storageAccounts@2022-09-01' = {
  name: storageAccountName
  location: location
  sku: {
    name: 'Standard_LRS'
  }
  kind: 'StorageV2'
  properties: {}
}
```

Now in your **main Bicep** file:

```bicep
// main.bicep
param location string = 'EastUS'

module storageModule './storage.bicep' = {
  name: 'deployStorageAccount'
  params: {
    storageAccountName: 'storagedemo01'
    location: location
  }
}
```

---

## 🧱 Example 2: Calling the Same Module Multiple Times

```bicep
param location string = 'EastUS'

var storageAccounts = [
  'storagedemo01'
  'storagedemo02'
]

resourceGroupName: 'my-rg'

module storageModules './storage.bicep' = [for name in storageAccounts: {
  name: 'deployStorageAccount-${name}'
  params: {
    storageAccountName: name
    location: location
  }
}]
```

➡️ This deploys multiple storage accounts using the **same module** with different parameters.

---

## 🔄 Why Use Modules?

- **Reusability**: Write once, reuse everywhere.
- **Separation of Concerns**: Different teams can manage different parts.
- **Organization**: Big deployments stay clean and understandable.
- **Simpler Maintenance**: Updating a module updates all places where it's used.

---

## ❌ Things to Keep in Mind

- The module must be deployed within the correct **scope** (resource group, subscription, etc.).
- If parameters are missing or mismatched, deployment will fail.
- Module deployment names must be **unique** in the same parent template.

---

## 🧠 Exam Tips

- Know how to structure and use modules in a Bicep file.
- Understand parameter passing between main templates and modules.
- Be aware of the **scope** where the module is deployed.
- Remember, modules **make templates cleaner** and **more maintainable**!

