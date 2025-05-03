# Availability Zones

Availability Zones help provide better availability for your application by protecting it from datacenter failures.

---

## 🌍 What Are Availability Zones?

- Each Availability Zone is a **unique physical location** within an Azure region.
- A zone consists of **one or more datacenters** with:
  - Independent **power**
  - Independent **cooling**
  - Independent **networking**

---

## 🛡️ Why Use Availability Zones?

- The **physical separation** between zones helps protect your applications from **datacenter-level failures**.
- They ensure **high availability and fault tolerance** for your resources.

---

## 💡 Key Point

- You can achieve up to **99.99% VM availability** when running your VMs across **2 or more Availability Zones** within the same region.

---

## 📌 Example Setup

- VM1 in **Zone 1**
- VM2 in **Zone 2**
- Load balancer in front to distribute traffic

This setup ensures the application stays available even if one zone goes down.

---

## 📝 Exam Tips

- Understand the difference between **Availability Zones** and **Availability Sets**.
- Know that Availability Zones provide **datacenter-level fault tolerance**.
- Be familiar with the **99.99% SLA** for VMs deployed across multiple zones.
- Remember that Availability Zones are specific to **supported Azure regions**.
- Be prepared to design solutions using Availability Zones for high availability and disaster recovery.

---

## 🔗 References

- [Availability Zones – Microsoft Docs](https://learn.microsoft.com/en-us/azure/availability-zones/az-overview)
