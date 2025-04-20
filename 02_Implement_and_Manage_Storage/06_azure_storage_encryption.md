# 🔐 Azure Storage Encryption

Azure Storage provides encryption for **data at rest** and **data in transit** to protect your data and meet security and compliance requirements.

---

## 🛡️ Data at Rest Encryption

- All data in Azure Storage (Blob, File, Queue, Table) is encrypted **automatically at rest** using **Storage Service Encryption (SSE)**.
- **No additional configuration** is required.
- Uses **256-bit AES encryption**, which is FIPS 140-2 compliant.

---

## 🔑 Encryption Key Management

Azure offers two options for managing encryption keys:

### 1. Microsoft-Managed Keys (Default)
- Azure automatically manages the encryption keys.
- Simplest and most commonly used method.
- Suitable for most use cases.

### 2. Customer-Managed Keys (CMK)
- You can use your own keys stored in **Azure Key Vault**.
- Gives more control over key rotation and access.
- Required for strict regulatory or compliance needs.
- Can be used with:
  - Azure Blob Storage
  - Azure Files (premium only)

---

## 🔐 Encryption Scenarios

| Scenario                    | Support    |
|-----------------------------|------------|
| Server-side encryption (SSE) | ✅ Enabled by default |
| Client-side encryption       | ✅ You must encrypt before uploading |
| Double encryption (SSE + CMK) | ✅ Optional for sensitive data |
| Encryption for data in transit | ✅ Enabled using HTTPS |

---

## 🔄 Key Rotation

- **Microsoft-managed keys** are automatically rotated by Azure.
- **Customer-managed keys** must be rotated manually or using Azure automation.
- You can set up **versioned keys** in Key Vault and update storage account references to the new version.

---

## 📘 Example Use Case

If you're in a regulated industry (e.g., finance, healthcare) and need full control over keys:
- Use **Customer-Managed Keys (CMK)**.
- Store them in **Azure Key Vault**.
- Rotate them regularly as per security policy.

---

## 🧠 Exam Tips

- SSE is **enabled by default** and cannot be turned off.
- CMK requires **Key Vault and proper permissions** (Storage account must be granted access to Key Vault).
- Understand difference between **Microsoft-managed vs Customer-managed keys**.
- Data in transit must use **HTTPS** to ensure encryption.

