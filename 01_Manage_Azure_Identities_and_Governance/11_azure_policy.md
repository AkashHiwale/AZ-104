# 🛡️ Azure Policy

Azure Policy is a service used to **create, assign, and manage policies** that enforce **rules and effects** on Azure resources. It helps in **governance, compliance, and standardization** of your Azure environment.

---

## 🎯 Purpose

- Enforce **organizational standards** and assess **compliance** at scale.
- Prevent the deployment of non-compliant resources.
- Audit existing resources and identify non-compliance.

---

## 🧱 Key Components

- **Policy Definition**: Describes what to audit or enforce (e.g., allowed locations).
- **Initiative Definition**: A group of policy definitions.
- **Assignment**: Attaches a policy or initiative to a scope (subscription, resource group, etc.).
- **Parameters**: Makes policy definitions reusable and flexible.

---

## 📦 Policy Effects

- **Deny**: Blocks the resource action.
- **Audit**: Logs non-compliance but doesn't block.
- **Append**: Adds settings to a resource.
- **DeployIfNotExists**: Deploys a resource if not already present.
- **AuditIfNotExists**: Audits when a specific resource is not present.

---

## 🔍 Compliance

- Azure Policy continuously evaluates resources for compliance.
- Shows **compliance state** in the Azure Portal.
- Resources that don't follow assigned policies are marked as **non-compliant**.

---

## 📌 Example Scenarios

- Restrict VM sizes in a region.
- Allow only tagged resources.
- Require diagnostic logs to be enabled.
- Enforce specific SKUs for services.

---

## 🛠️ Management Tools

- Azure Portal (Policy Blade)
- Azure CLI  
  ```bash
  az policy assignment create --name <name> --policy <policyDefinitionId> --scope <scope>
  ```
- PowerShell  
  ```powershell
  New-AzPolicyAssignment -Name <name> -PolicyDefinition <definition> -Scope <scope>
  ```
- REST API / ARM templates / Bicep

---

## 🧠 Exam Tips

- Understand **Deny vs Audit** effect.
- Know how to assign policies and what scope means.
- Be familiar with **DeployIfNotExists** for compliance automation.
- Remember that **Initiatives** group multiple policies for broader governance.
- Know that **Azure Policy evaluates both new and existing resources**.
