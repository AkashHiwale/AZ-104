# Custom Script Extension

The **Custom Script Extension** is used to **automate the execution of scripts on a VM after deployment**. This is helpful for installing applications or performing configuration tasks.

## ✅ Key Points

- Executes a script (PowerShell, Bash, etc.) provided via URL or storage.
- Runs during or after the deployment phase.
- Ideal for automation in **ARM templates**, **Bicep**, or **Terraform**.

## 📌 Example Use Case

Install **NGINX** on a Linux VM after provisioning:

```bash
#!/bin/bash
sudo apt update
sudo apt install nginx -y
```

You can reference this script via a URL in your deployment template or Azure CLI.

## 🔗 References

- [Custom Script Extension (Microsoft Docs)](https://learn.microsoft.com/en-us/azure/virtual-machines/extensions/custom-script-linux)