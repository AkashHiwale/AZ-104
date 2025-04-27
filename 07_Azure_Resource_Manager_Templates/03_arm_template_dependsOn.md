# 🧑‍💻 ARM Template - dependsOn

---

## 📌 What is dependsOn?

- The dependsOn element in ARM templates is used to specify the order of resource deployment.
- It ensures that one resource is deployed only after the successful creation of other resources.
- This is crucial when resources depend on each other for proper configuration.

---

## 🛠️ Syntax for dependsOn

- dependsOn is specified as an array within the resource definition.
- It allows you to list the dependent resources by their resource IDs.

> Add dependsOn inside a resource's definition when you need to specify that the resource depends on another resource.

Example for adding dependsOn in a storage account resource:

``` json
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
      "dependsOn": [
        "[resourceId('Microsoft.Resources/resourceGroups', 'rg-demo')]"
      ],
      "sku": {
        "name": "Standard_LRS"
      },
      "kind": "StorageV2"
    }
  ]
}
```

---

## 🧱 How dependsOn Works

- **Automatic Dependency Handling**: If resources reference each other directly, the dependsOn is automatically inferred. However, if indirect dependencies exist, you must specify them using dependsOn.
- **Execution Order**: By default, resources in ARM templates are deployed in parallel. The dependsOn property ensures sequential execution, where necessary.

## 🧠 Use Cases for dependsOn

1. **Resource Creation Order**:
   - When you need to ensure that one resource is created before another, e.g., a storage account before a virtual machine using that storage.
   
2. **Resource Dependencies with Nested Resources**:
   - Nested resources (like virtual machine extensions) often depend on the parent resource being created first.

3. **Enforcing Order of Execution**:
   - In cases where resources don't have explicit references but still need to be deployed in a specific order.


---

## ❌ Limitations of dependsOn

- **No Impact on Resource Updates**: The dependsOn only affects the creation order of resources, not their update order.
- **Not for Runtime Dependencies**: dependsOn is evaluated only at deployment time and does not affect the runtime behavior of resources.

---

## 🧠 Exam Tips

- Understand the basic use of dependsOn to ensure correct resource deployment order.
- Know how to reference a resource ID in dependsOn.
- Be aware of automatic dependencies that Azure handles without needing explicit dependsOn.
