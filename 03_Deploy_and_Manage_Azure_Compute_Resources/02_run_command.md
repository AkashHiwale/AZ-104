# Run Command

**Run Command** lets you **execute scripts directly from the Azure Portal, CLI, or PowerShell** on an existing VM. It's useful for one-off tasks or remote troubleshooting.

## ✅ Key Points

- Doesn’t require prior deployment setup.
- Runs immediately from the portal.
- Good for quick, ad-hoc administrative tasks.

## 📌 Example Use Case (Windows Server)

Install IIS (Internet Information Services):

```powershell
Import-Module ServerManager
Add-WindowsFeature Web-Server -IncludeAllSubFeature
```

This can be run via:
- Azure Portal > Virtual Machines > [Your VM] > Run Command
- Azure CLI: `az vm run-command invoke`

## 🔗 References

- [Run Command Overview](https://learn.microsoft.com/en-us/azure/virtual-machines/windows/run-command)