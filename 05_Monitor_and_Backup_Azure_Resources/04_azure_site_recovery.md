
# 🌐 Azure Site Recovery (ASR)

---

## 📌 What is Azure Site Recovery?

- Azure Site Recovery (ASR) is a **disaster recovery (DR)** solution.
- It **replicates** workloads running on:
  - Physical servers
  - Azure VMs
  - On-premises VMs (like Hyper-V or VMware)
- In case of an outage, you can **failover** to a secondary location and **failback** when normal operations resume.

---

## ⚙️ Key Components

- **Source Location**: The original server or VM to be protected.
- **Target Location**: The location where the workloads will fail over to (e.g., Azure region).
- **Recovery Services Vault**: A management entity that holds backup and disaster recovery data.
- **Mobility Service**: A lightweight agent installed on VMs to replicate data to Azure.
- **Process Server** (for on-premises VMware): Handles data transfer between the source machine and Azure.

---

## 🛠️ How it Works

1. **Prepare infrastructure** at both source and target.
2. **Enable replication** of virtual machines or servers.
3. **Monitor replication health** and test failovers.
4. **Failover** during a real outage or **planned failover** during maintenance.
5. **Failback** once the primary site is back online.

---

## 🔥 Important Features

- **Replication Frequency**: Near real-time.
- **Recovery Plans**: Orchestrate the failover and recovery of multiple VMs.
- **DR Drills**: Test your disaster recovery plans without impacting production.
- **Multi-VM Consistency**: Ensure apps across multiple VMs stay consistent.

---

## 🧠 Exam Tips

- **Recovery Services Vault** is critical for managing replication and recovery.
- Know **difference between failover and failback**.
- Understand **Recovery Plans** for orchestrating failover of multiple VMs.
- **Site Recovery** can protect VMs within Azure (region-to-region) as well.

---

## ⚡ Quick Example

- Protect a VMware virtual machine hosted on-premises by replicating it to Azure.
- In case the on-premises datacenter fails, initiate a **failover** to Azure.
- When the datacenter is restored, **failback** the machine from Azure to on-premises.
