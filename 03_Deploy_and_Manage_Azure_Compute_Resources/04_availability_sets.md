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

## 📌 Summary

| Component        | Description                                                        | Max Limit         |
|------------------|--------------------------------------------------------------------|-------------------|
| Availability Set | Logical grouping of VMs for higher availability                   | N/A               |
| Fault Domain     | Protects against power/network hardware failures                   | Up to 3           |
| Update Domain    | Protects from planned maintenance reboots                          | Up to 20          |

---

## 🔗 References

- [Availability Sets – Microsoft Docs](https://learn.microsoft.com/en-us/azure/virtual-machines/availability-set-overview)
