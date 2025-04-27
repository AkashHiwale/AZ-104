# 🧑‍💻 ARM Template Variables

---

## 📌 What are ARM Template Variables?

Variables in ARM Templates help you store values that are used multiple times.

They allow you to simplify your template and avoid repetition.

Variables are evaluated once when the template is deployed.

---


## 🛠️ Syntax for Variables

Variables are defined under the variables section in an ARM template.

``` json
{
    "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#", 
    "contentVersion": "1.0.0.0", 
    "variables": { 
        "variableName": "value" 
    }, 
    "resources": [] 
}
```
---


## 🧱 Example of Variables

Here’s a simple example where we define variables for resource names and tags:

``` json
{ 
    "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#", 
    "contentVersion": "1.0.0.0", 
    "variables": { 
        "resourceGroupName": "rg-demo", 
        "storageAccountName": "storagedemo123", 
        "location": "EastUS" 
    }, 
    "resources": [ 
        { 
            "type": "Microsoft.Resources/resourceGroups",
            "apiVersion": "2019-05-10", 
            "location": "[variables('location')]", 
            "properties": {} 
        }, 
        {   "type": "Microsoft.Storage/storageAccounts", 
            "apiVersion": "2019-06-01", 
            "name": "[variables('storageAccountName')]", 
            "location": "[variables('location')]", 
            "sku": { 
                "name": "Standard_LRS" 
            }, 
            "kind": "StorageV2" 
        } 
    ] 
}
```
---


## 🔄 How to Use Variables

Variables can be referenced using the following syntax: `[variables('variableName')]`

You can use variables throughout the template wherever a value is required.
---

## 🧠 Key Use Cases of Variables

- **Avoid Redundancy**:  
Use variables to store repeated values (like names, locations, etc.), which can reduce mistakes and make templates more readable.

- **Parameterize Values**:  
Use variables to make your template dynamic. For instance, you can use a variable for a prefix that you can later reference in multiple places.

- **Set Default Values**:  
Set default values in the variables section and use them if the parameters section is not supplied during deployment.

---


## ❌ Limitations of Variables

- Variables are **immutable**. Once defined, their values cannot be changed within the template.

- Variables can only be **evaluated at deployment time** and are not available for further updates or dynamic changes during runtime.

---


## 🧠 Exam Tips

- Understand the **syntax for defining and referencing variables** in ARM templates.

- Variables are useful when you need to **repeat values** (e.g., location, resource names).

- Know how to use **variables with resources** and within expressions.

