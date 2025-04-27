# 🧑‍💻 Creating Multiple Storage Accounts Using Bicep

---

## 📌 Why Create Multiple Resources?

- Sometimes you need to deploy **multiple identical resources** (like storage accounts) with slight variations.
- Instead of manually duplicating resource definitions, you can use **loops** (`for` expressions) in Bicep to simplify your deployment.

---

## 🛠️ Syntax for Multiple Copies

- Bicep supports loops with the `for` keyword inside the `resource` block.
- You can dynamically create resources based on an array or a range.

> Add a `for` loop inside your resource block to create multiple resources at once.

Example structure:

```bicep
resource <resourceName> 'ResourceType@apiVersion' = [for <item> in <collection>: {
  name: ...
  properties: ...
}]
```

---

## 🧱 Example 1: Creating Multiple Storage Accounts from an Array

```bicep
param location string = 'EastUS'

var storageAccountNames = [
  'storagedemo01'
  'storagedemo02'
  'storagedemo03'
]

resource storageAccounts 'Microsoft.Storage/storageAccounts@2022-09-01' = [for name in storageAccountNames: {
  name: name
  location: location
  sku: {
    name: 'Standard_LRS'
  }
  kind: 'StorageV2'
  properties: {}
}]
```

➡️ This will create three storage accounts with names defined in `storageAccountNames`.

---

## 🧱 Example 2: Creating Storage Accounts with Index Suffix

```bicep
param location string = 'EastUS'

resource storageAccounts 'Microsoft.Storage/storageAccounts@2022-09-01' = [for i in range(0, 3): {
  name: 'storagedemo${i}'
  location: location
  sku: {
    name: 'Standard_LRS'
  }
  kind: 'StorageV2'
  properties: {}
}]
```

➡️ This will create storage accounts named:
- `storagedemo0`
- `storagedemo1`
- `storagedemo2`

---

## 🔄 When to Use Loops in Bicep

- When **creating many similar resources** with minor differences.
- To **avoid copy-pasting** multiple resource blocks manually.
- To **keep templates clean and dynamic**.

---

## ❌ Things to Keep in Mind

- Resource names must still be unique across Azure.
- Be cautious when looping — errors are harder to debug if the loop logic is wrong.
- The range or array should be properly controlled to avoid excessive resource creation.

---

## 🧠 Exam Tips

- Know how `for` loops work in Bicep for deploying multiple resources.
- Understand the difference between looping over an array vs. using a range.
- Be familiar with resource property interpolation like `'storagedemo${i}'`.

