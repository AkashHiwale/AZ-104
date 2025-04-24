# 🏷️ Azure Resource Tags

---

## 📌 What are Resource Tags?

- Tags are **name-value pairs** assigned to Azure resources.
- Help in **organizing**, **categorizing**, and **managing** Azure resources.
- Tags can be applied to:
  - Resource groups
  - Individual resources
  - Subscriptions
- Useful for **cost tracking**, **automation**, **governance**, and **resource filtering**.

---

## 🧱 Tag Structure

- Tags consist of a **Key** and a **Value**.
  - Example: `Environment = Production`
- A resource can have **up to 50 tags**.
- Maximum length:
  - **Key**: 512 characters (128 for some services)
  - **Value**: 256 characters

---

## 🧠 Use Cases

- **Cost Management**: Tag by department, project, or cost center.
- **Automation**: Use tags to trigger scripts or apply policies.
- **Governance**: Enforce naming and tagging standards using Azure Policy.
- **Environment Management**: Easily filter Dev/Test/Prod environments.

---

## 🛠️ How to Apply Tags

- Azure Portal
- Azure CLI  
  ```bash
  az tag create --resource-id <resource_id> --tags Environment=Dev Owner=TeamA
  ```
- PowerShell  
  ```powershell
  Set-AzResource -ResourceId <resource_id} -Tag @{Environment="Dev"; Owner="TeamA"} -Force
  ```
- ARM templates, Bicep, and Terraform

---

## 🔍 Viewing and Managing Tags

- Azure Portal: Tags tab on the resource page
- Azure Cost Management: Filter cost by tag
- Azure Resource Graph: Query tags across subscriptions

---

## ❌ Limitations

- Tags are **not inherited** from Resource Groups to Resources.
- Not all resources support tagging at creation time.
- Tags are **case-insensitive** but stored as entered.

---

## 🧠 Exam Tips

- Know that **tags do not enforce policy**, but they can be **used with Azure Policy** to enforce tagging rules.
- Be familiar with tag **limits** and **use cases** (like cost tracking).
- Understand **how to apply tags** using CLI and PowerShell.
