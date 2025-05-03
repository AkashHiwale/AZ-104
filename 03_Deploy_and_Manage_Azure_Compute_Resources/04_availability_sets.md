# Availability Sets

Availability Sets are a logical grouping of virtual machines that help reduce the chances of multiple VMs going down due to hardware failure.

---

## 🧱 What Are Availability Sets?

- Used to increase the **availability** of your application.
- When you assign VMs to an availability set, each VM is automatically placed in a **separate fault domain** and **update domain**.
- This ensures your VMs are distributed across isolated infrastructure resources.

---

## ⚡ Fault Domains

- Fault domains define a group of machines that **share a common power source and network switch**.
- This setup helps protect against **hardware failures**.
- Azure allows up to **3 fault domains** (depending on the region).

---

## 🔄 Update Domains

- Update domains define a group of VMs and physical hosts that can be **rebooted at the same time**.
- Used during **planned maintenance** to ensure not all VMs go down together.
- Azure supports up to **20 update domains**.

---

## 📌 Example: Availability Set in Action

Imagine you are deploying a web application that requires high availability. You create an **Availability Set** and assign three VMs to it:

1. **VM1** is placed in Fault Domain 1 and Update Domain 1.
2. **VM2** is placed in Fault Domain 2 and Update Domain 2.
3. **VM3** is placed in Fault Domain 3 and Update Domain 3.

This setup ensures:
- If a hardware failure occurs in Fault Domain 1, only **VM1** is affected.
- During planned maintenance, only one Update Domain is rebooted at a time, ensuring at least two VMs remain operational.

---

## 📌 Summary

| Component        | Description                                                        | Max Limit         |
|------------------|--------------------------------------------------------------------|-------------------|
| Availability Set | Logical grouping of VMs for higher availability                   | N/A               |
| Fault Domain     | Protects against power/network hardware failures                   | Up to 3           |
| Update Domain    | Protects from planned maintenance reboots                          | Up to 20          |

---

## 📝 Exam Tips

- Understand the purpose of **Availability Sets** and how they improve availability.
- Know the difference between **Fault Domains** and **Update Domains**.
- Be familiar with the maximum limits for fault domains (3) and update domains (20).
- Remember that Availability Sets are specific to a **single region** and **single availability zone**.
- Be prepared to design solutions that require high availability using Availability Sets.

---

## 🔗 References

- [Availability Sets – Microsoft Docs](https://learn.microsoft.com/en-us/azure/virtual-machines/availability-set-overview)
