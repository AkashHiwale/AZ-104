# 🔐 Microsoft Entra ID – External Identities, Licensing, and SSPR

---

## 🤝 Inviting External Identities (Guest Users)

- Microsoft Entra ID supports **B2B (Business-to-Business)** collaboration.
- You can invite **external users (guests)** to your tenant using:
  - Azure Portal
  - PowerShell
  - Microsoft Graph
- Invited users receive an email to accept the invitation.
- External users are represented as **UserType = Guest** in the directory.
- Access can be controlled using **Conditional Access**, **Groups**, and **RBAC**.

### ✅ Use Cases:
- Collaborating with partners, vendors, contractors.
- Giving limited access to apps or resources.

---

## 📄 Microsoft Entra ID Licenses

There are **3 main tiers**:

| Tier              | Features Included                                                    |
|-------------------|----------------------------------------------------------------------|
| **Free**          | Basic user and group management, device registration                 |
| **P1 (Premium 1)**| Conditional Access, Group-based licensing, SSPR, MFA, Hybrid Join     |
| **P2 (Premium 2)**| All P1 features + Identity Protection, Privileged Identity Management (PIM) |

---

## 🎓 Premium Trial License

- You can activate a **30-day trial** for P1 or P2 from the **Microsoft Entra admin center**.
- Allows testing of premium features without purchase.


### 🛠️ Steps to Activate Premium P2 Trial License

1. Go to **https://entra.microsoft.com**.
2. Sign in with your Azure AD admin account.
3. In the left menu, go to **Billing → Licenses → All Products**.
4. Click on **"Try/Buy"**.
5. Select **Microsoft Entra ID P2**.
6. Click **"Activate"** to start your 30-day trial.

---

## 👥 Assigning Licenses to Users and Groups

- Licenses can be assigned to:
  - Individual users
  - Groups (Recommended for scale)
- If assigned to a group:
  - Any user added to the group automatically inherits the license.
  - When removed, the license is revoked.
- Group-based licensing helps in **automation and consistency**.

---

## 🔑 Self-Service Password Reset (SSPR)

- Allows users to **reset their password** without admin intervention.
- Can be enabled for:
  - None
  - Selected users
  - All users
- Requires users to register **authentication methods** (like phone, email, security questions).
- Admins can configure:
  - Number of methods required for reset
  - Notification on reset
  - Lockout settings

### ✅ Benefits:
- Reduces helpdesk calls
- Improves user productivity

---

## 🧠 Exam Tips

- Understand **UserType = Guest** for external identities.
- Know the difference between **Free, P1, P2** licenses.
- Group-based licensing is available only with **Premium licenses**.
- You can activate a **trial license** for 30 days for P1/P2 features.
- SSPR is a **premium feature** and can be scoped to selected users.
