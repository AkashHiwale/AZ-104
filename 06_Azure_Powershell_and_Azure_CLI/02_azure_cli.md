
# 🚀 Azure CLI Notes

---

## 📌 What is Azure CLI?

- Azure CLI is a **command-line tool** to manage Azure resources.
- Runs on **Windows**, **Linux**, **macOS**, and is available in **Azure Cloud Shell**.
- Commands start with `az`.

---

## 🛠️ Common Azure CLI Commands

| **Action**                  | **Command Example**  |
|-------------------------------|-----------------------|
| Login to Azure                | `az login`             |
| Set active subscription       | `az account set --subscription "<SubscriptionName>"` |
| Create a Resource Group       | `az group create --name rg-demo --location eastus` |
| List Resource Groups          | `az group list`        |
| Delete a Resource Group       | `az group delete --name rg-demo` |
| Create a Virtual Network      | `az network vnet create --name vnet-demo --resource-group rg-demo --address-prefix 10.0.0.0/16 --subnet-name subnet-demo --subnet-prefix 10.0.0.0/24` |
| View Virtual Network Details  | `az network vnet show --name vnet-demo --resource-group rg-demo` |
| Create a VM                   | `az vm create -g "app-grp" -n "appvm" --image Win2022Datacenter --admin-username "appusr"` |
| Create a Data Disk            | `az disk create -n "data-disk" -g "app-grp" -l "North Europe" --size-gb 16` |
| Attach Data Disk to VM        | `az vm disk attach --vm-name "appvm" --lun 0 -g "app-grp" -n "data-disk"` |
| Create Storage Account        | `az storage account create -n "newstore44333" -g "app-grp" --kind "StorageV2" --sku "Standard_LRS"`|
| Create App Service Plan       | `az appservice plan create -n "demoplan4434" -g "app-grp" --sku F1`|
| Create Web App                | `az webapp create -n "webapp5434" -g "app-grp" --plan "demoplan4434"`|
| Create VM Scale Set           | `az vmss create -n "app-set" -g "app-grp" --admin-username "appusr" --image Win2022Datacenter --vm-sku "Standard_DS2_v2" `|

---

## 🧠 Exam Tips

- **Know the structure**: Azure CLI commands start with `az`, followed by the resource type, then the action.
  - Example: `az vm create`
- **Understand authentication**:
  - `az login` — to log in interactively.
  - `az account set` — to set a specific subscription.
- **Available in Azure Cloud Shell**:
  - No installation required.
  - Always has latest Azure CLI updates.

- **Syntax Difference**:  
  - CLI: Uses `--parameters`
  - PowerShell: Uses `-Parameters`
  
- **Automation Friendly**:  
  Azure CLI works great with Bash scripts for automation.

---

## 🌐 Installation

- Install Azure CLI locally:  
  - Windows: MSI installer.
  - macOS: Homebrew.
  - Linux: Package managers (APT, YUM, etc.)

- Official documentation for install:  
  [Install Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli)

---

## ❗ Important Points

- Azure CLI outputs JSON by default (can change to table or TSV).
- Commands are **idempotent** — safe to re-run without unintended side effects.
- You can use **`--help`** at any point:
  ```bash
  az vm create --help
  ```
