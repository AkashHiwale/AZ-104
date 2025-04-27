
# 🧑‍💻 ARM Template - parameters

---

## 📌 What are Parameters?

- Parameters in ARM templates are used to define dynamic input values that can be provided during template deployment.
- They make templates reusable by allowing the same template to be deployed in different environments with different values (e.g., different VM sizes, locations).
- Parameters allow flexibility in the configuration of resources and enable you to customize deployments without altering the template itself.

---

## 🛠️ Syntax for Parameters

- Parameters are defined under the `parameters` section in the ARM template.
- You can specify parameter types, allowed values, default values, and descriptions for each parameter.

> Add the `parameters` section to define input values for your template that can be passed at deployment time.

Example for defining a parameter for the virtual machine size:

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "parameters": {
    "vmSize": {
      "type": "string",
      "defaultValue": "Standard_DS2_v2",
      "allowedValues": [
        "Standard_B1s",
        "Standard_DS2_v2",
        "Standard_F4s"
      ],
      "description": "The size of the virtual machine."
    },
    "location": {
      "type": "string",
      "defaultValue": "EastUS",
      "allowedValues": [
        "EastUS",
        "WestUS",
        "NorthEurope"
      ],
      "description": "The location for the resources."
    }
  },
  "resources": []
}
```

---

## 🧱 How Parameters Work

- **Dynamic Deployment**: During deployment, values for the parameters can be passed. If not provided, default values are used.
- **Template Flexibility**: Parameters make templates reusable across different projects or environments by allowing you to specify different values during deployment.

---

## 🧠 Use Cases for Parameters

1. **Dynamic Template Configuration**:
   - When you need to specify different values (like VM size or location) at deployment time, use parameters for a more flexible and reusable template.
   
2. **Customizing Deployments**:
   - Parameters allow the same template to be used in multiple environments by specifying different values (e.g., for dev, test, production environments).
   
3. **Reducing Template Duplication**:
   - Instead of writing multiple templates for different environments, you can create one template with parameters and use it for various deployments with different values.

---

## ❌ Limitations of Parameters

- **No Logic**: Parameters do not support conditional logic. For logic, you should use functions or variables.
- **No Updates After Deployment**: Parameters are set during deployment and cannot be changed afterward without redeploying the template.

---

## 🧠 Exam Tips

- Understand the basic syntax for defining parameters and how they are referenced in the template.
- Know how to set default values, allowed values, and descriptions for parameters.
- Understand how parameters allow for dynamic configurations and reusable templates.

