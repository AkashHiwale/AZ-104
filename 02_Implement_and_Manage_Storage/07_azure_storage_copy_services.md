# 🔄 Azure Storage Copy Services

Azure provides multiple tools and services to **transfer data to and from storage accounts** efficiently. Two of the most commonly used options are:

---

## 📦 Azure Import/Export Service

### What it is:
- A service to **securely transfer large amounts of data** to or from Azure using **physical hard drives**.

### How it works:
1. Prepare your disk with data.
2. Use Microsoft’s **WAImportExport** tool to write or read data.
3. Ship the disk to the Microsoft datacenter.
4. Microsoft uploads/downloads data to/from your Azure Storage account.

### Use Cases:
- When transferring **terabytes or petabytes** of data.
- **Slow or expensive network** makes online transfer impractical.

### Key Points:
- Supports **Blob Storage** and **Azure Files**.
- Data is **AES-encrypted** before shipping.
- You can track job status via the **Azure Portal**.

---

## ⚙️ AzCopy Tool

### What it is:
- A **command-line utility** for high-performance data transfers between:
  - **Local systems** and Azure Storage
  - **Between containers**
  - **Between storage accounts**

### Key Features:
- Cross-platform: **Windows, Linux, macOS**
- **Parallel and resumable** transfers
- Supports **Blob and File storage**
- Can authenticate using:
  - **SAS tokens**
  - **Azure AD**
  - **Storage account keys**

### Common Commands:

```bash
# Upload a local file to Azure Blob
azcopy copy "C:\data\file.txt" "https://<account>.blob.core.windows.net/<container>?<SAS-token>"

# Download from Azure Blob
azcopy copy "https://<account>.blob.core.windows.net/<container>/file.txt?<SAS-token>" "C:\downloads\"

# Sync local folder to blob container
azcopy sync "C:\data\" "https://<account>.blob.core.windows.net/<container>?<SAS-token>"
```

---

## 🧠 Exam Tips: Azure Storage Copy Services

- ✅ Use **Import/Export** for **large offline data transfers** (terabytes or petabytes).
- ⚡ Use **AzCopy** for **fast online transfers**, especially for **script-based** or **automated solutions**.
- 🔐 **AzCopy supports authentication via**:
  - SAS Tokens
  - Azure Active Directory (Azure AD)
  - Connection Strings
