# 👤 Microsoft Entra ID (Azure AD)

Microsoft Entra ID is **Microsoft’s cloud-based identity and access management (IAM) service**.  
It helps employees sign in and access resources like:
- Microsoft 365
- Azure portal
- SaaS applications (e.g., Salesforce)
- On-prem apps (via Azure AD Application Proxy)

---

## ✅ Key Features

### 1. **Authentication**
- Supports **single sign-on (SSO)**
- **Multi-Factor Authentication (MFA)** for added security

### 2. **Authorization**
- Role-Based Access Control (**RBAC**) using **built-in** or **custom roles**

### 3. **Directory Services**
- Manages **users, groups, devices, and service principals**

### 4. **Self-Service Capabilities**
- Password reset
- Group management
- App access requests

### 5. **Device Management**
- Registers devices to enable conditional access

---

## 🛡️ Security Features

| Feature                  | Description |
|--------------------------|-------------|
| **Conditional Access**   | Automates access decisions based on conditions like user location, device compliance |
| **MFA**                  | Requires additional verification like OTP, biometrics, etc. |
| **Identity Protection**  | Uses machine learning to detect risky logins |
| **Privileged Identity Management (PIM)** | Controls and monitors access to critical resources |

---

## 👥 Users and Groups

### Users
- Can be cloud-only or synced from on-prem AD via **Azure AD Connect**

### Groups
- **Security groups** – used for assigning access
- **Microsoft 365 groups** – used for collaboration
- Supports **dynamic groups** (rule-based membership)

---

## 🔗 External Identities
- Allows **B2B collaboration** (business partners, vendors)
- Users can access shared resources using their own credentials

---

## 📄 Licensing Tiers

| Tier            | Features |
|------------------|----------|
| **Free**         | Basic user and group management, directory sync |
| **P1 (Premium)** | Conditional Access, group-based licensing, self-service password reset |
| **P2 (Premium)** | Identity Protection, PIM |

---

## 🧠 Exam Tips

- Know the **difference between roles and groups**.
- Understand **Conditional Access policies** and when to apply them.
- MFA and **SSPR (Self-Service Password Reset)** are commonly tested.
- Recognize the difference between **Azure AD** (now Entra ID) and **Active Directory Domain Services (AD DS)**.
- Be familiar with **external identity use cases**.

---

