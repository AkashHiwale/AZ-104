# 🧑‍💻 ARM Template - Copy

---

## 📌 What is Copy in ARM Templates?

- The `copy` element in ARM templates is used to create multiple instances of a resource or nested resource in a template.
- It allows you to efficiently deploy resources that are similar but need to be created multiple times, such as multiple virtual machines or network interfaces, without duplicating the resource definitions.
- It uses the `copy` loop to repeat resource definitions, which helps simplify templates and avoid redundancy.

---

## 🛠️ Syntax for Copy

- The `copy` element is added to a resource or nested resource definition and specifies how many instances to create.
- You must specify a name for the `copy` element and the number of times to repeat the resource using the `count` property.
- You can also use `name` or `range` properties to dynamically generate names for each instance.

> Add copy when you need to deploy multiple instances of similar resources.

### Example for creating multiple virtual machines using `copy`:

``` json
{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "resources": [
    {
      "type": "Microsoft.Compute/virtualMachines",
      "apiVersion": "2021-04-01",
      "name": "[format('vm{0}', copyIndex())]",
      "location": "EastUS",
      "properties": {
        "hardwareProfile": {
          "vmSize": "Standard_DS1_v2"
        },
        "storageProfile": {
          "imageReference": {
            "publisher": "MicrosoftWindowsServer",
            "offer": "WindowsServer",
            "sku": "2019-Datacenter"
          }
        },
        "osProfile": {
          "computerName": "[format('vm{0}', copyIndex())]",
          "adminUsername": "adminuser",
          "adminPassword": "password123!"
        }
      },
      "copy": {
        "name": "vmCopy",
        "count": 3
      }
    }
  ]
}
```

---

## 🧱 How Copy Works

- **`copy` Element**: This element is used to define how many copies of a resource or nested resource should be created.
- **`copyIndex()` Function**: The `copyIndex()` function is used to create unique names or configurations for each copy of the resource.
- **Repeat Resources**: The `count` property in the `copy` element defines how many times the resource or nested resource will be created.

---

## 🧠 Use Cases for Copy

1. **Deploying Multiple Identical Resources**:
   - Use the `copy` element when you need to deploy several similar resources, like multiple virtual machines or network interfaces, without repeating the entire resource definition.
   
2. **Scaling Resources**:
   - It is commonly used when deploying scalable resources like storage accounts or web apps that need to be created in multiple instances.

3. **Creating Arrays of Resources**:
   - When you want to create an array of resources with similar configurations but with slightly different properties (e.g., VM names or IP addresses).

---

## ❌ Limitations of Copy

- **Limited Dynamic Creation**: `copy` only allows for repetitive creation based on count or range, so it cannot dynamically change based on external input at runtime.
- **No Nested Loops**: The `copy` element cannot be used to create nested copies inside other resources (i.e., looping inside a loop is not supported directly).

---

## 🧠 Exam Tips

- Understand the use of `copy` to deploy multiple identical or similar resources efficiently.
- Be able to use `copyIndex()` to create dynamic names for each instance.
- Know when to use `count` for repeating resources and how it simplifies the template.

