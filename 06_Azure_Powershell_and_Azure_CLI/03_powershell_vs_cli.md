# ⚡ Azure PowerShell vs Azure CLI (Exam Perspective)

---

## 🧩 Overview

| Aspect | Azure PowerShell | Azure CLI |
|:------|:-----------------|:---------|
| Language | PowerShell scripting language (cmdlets) | Bash-style commands (cross-platform) |
| Usage | Ideal for users familiar with PowerShell | Ideal for users comfortable with Bash or scripting |
| Platform Support | Windows, macOS, Linux | Windows, macOS, Linux |
| Integration | Deep integration with Windows PowerShell | Native cross-platform support |
| Learning Curve | Slightly steeper if new to PowerShell | Simpler and straightforward syntax |
| Azure Cloud Shell | Available (pre-installed Az module) | Available (pre-installed CLI tool) |
| Automation | Best for complex workflows with scripting | Best for quick automation and lightweight scripts |
| Examples | `New-AzVM` | `az vm create` |

---

## 🔥 Key Differences

- **Syntax**
  - PowerShell uses **cmdlet** style (Verb-Noun):  
    `New-AzResourceGroup`
  - CLI uses simpler command style:  
    `az group create`

- **Automation Suitability**
  - PowerShell is better suited for **advanced scripting**, error handling, and **workflow automation**.
  - Azure CLI is faster for **quick, interactive tasks**.

- **Installation**
  - Both tools can be installed locally.
  - Both are available pre-installed in **Azure Cloud Shell**.

---

## 🧠 Exam Tips

- Know **basic syntax** of both Azure PowerShell and Azure CLI.
- Recognize the difference in how commands look:
  - PowerShell: `New-AzVM`
  - CLI: `az vm create`
- Understand that:
  - **PowerShell** is often used for **complex automation** and **administration scripts**.
  - **CLI** is ideal for **simple**, **quick tasks** and lightweight automation.
- Cloud Shell has both tools available — **no local installation required**.
- Be ready to **identify a script** as CLI or PowerShell based on the syntax in exam questions.

