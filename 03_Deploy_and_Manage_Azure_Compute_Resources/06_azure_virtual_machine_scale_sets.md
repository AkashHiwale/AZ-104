# Azure Virtual Machine Scale Sets (VMSS)

Azure Virtual Machine Scale Sets help you to create and manage a group of **load-balanced virtual machines**.

---

## ⚙️ What Does It Do?

- Lets you deploy and manage a set of identical VMs.
- The number of virtual machines can **automatically grow or shrink** based on:
  - **Demand** (autoscaling)
  - A **defined schedule** (manual or scheduled scaling)

---

## 📈 Why Use VMSS?

- Helps with **scalability** – user traffic can be **distributed across multiple VMs** to handle load efficiently.
- Ideal for **high-availability** and **auto-recovery** scenarios.

---

## 🔧 Scaling Options

| Mode    | Description                                        |
|---------|----------------------------------------------------|
| Uniform | Scaling is **fully managed by Azure**              |
| Manual  | You **control scaling manually**                   |

---

## 📝 Exam Tips

- Understand how **autoscaling** works in VMSS and the difference between **demand-based scaling** and **scheduled scaling**.
- Know the benefits of **Uniform** versus **Manual** scaling modes.
- Be familiar with how VMSS integrates with **load balancers** for traffic distribution.
- Remember that VMSS ensures **high availability** and supports **auto-recovery**.
- Be prepared to design solutions that require **scalability** and **fault tolerance** using VMSS.

---

## 🔗 References

- [Azure Virtual Machine Scale Sets – Microsoft Docs](https://learn.microsoft.com/en-us/azure/virtual-machine-scale-sets/overview)
