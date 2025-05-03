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

## 📝 Exam Tips

- Understand how to use the **Custom Script Extension** in **ARM templates**, **Bicep**, and **Terraform**.
- Be familiar with the process of referencing scripts via a URL or Azure Storage.
- Know the difference between running scripts during deployment versus post-deployment.
- Remember that the extension supports both **Windows** and **Linux** VMs.
- Be prepared to troubleshoot common issues, such as script execution failures or incorrect permissions.

## 🔗 References

- [Custom Script Extension (Microsoft Docs)](https://learn.microsoft.com/en-us/azure/virtual-machines/extensions/custom-script-linux)