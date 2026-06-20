# Day 3 — Storage & RAID

<p align="center">
  <img src="https://img.shields.io/badge/Level-Intermediate-d29922?style=for-the-badge" alt="Level: Intermediate">
  <img src="https://img.shields.io/badge/Track-Server%20Hardware-1f6feb?style=for-the-badge" alt="Track: Server Hardware">
  <img src="https://img.shields.io/badge/Module-3%20of%207-8957e5?style=for-the-badge" alt="Module 3 of 7">
</p>

<p align="center">
  <b>Goal:</b> Understand storage media types, how they connect, and how RAID delivers performance and redundancy.
</p>

---

## Topics in This Module

1. [Storage Media Types](#31--storage-media-types)
2. [Storage Interfaces Deep Dive](#32--storage-interfaces-deep-dive)
3. [RAID Levels](#33--raid-levels)
4. [Controllers, Hot Spare & Hot Swap](#34--controllers-hot-spare--hot-swap)

---

# 3.1 — Storage Media Types

Servers choose storage by balancing:

* Cost
* Capacity
* Speed
* Endurance

```mermaid
flowchart LR

    HDD[HDD - Spinning Disk]
    SSD[SSD - Flash]
    NVME[NVMe - Flash over PCIe]

    HDD --> CAP[High Capacity / Low Cost]
    SSD --> BAL[Balanced Speed]
    NVME --> FAST[Lowest Latency / Highest IOPS]
```

| Media              |   Speed   | Cost / GB | Best For                           | Failure Risk    |
| ------------------ | :-------: | :-------: | ---------------------------------- | --------------- |
| **HDD**            |    Low    |   Lowest  | Bulk storage, backups              | Mechanical wear |
| **SSD (SATA/SAS)** |    High   |   Medium  | General-purpose workloads          | Flash wear      |
| **NVMe**           | Very High |   Higher  | Databases, caching, virtualization | Flash wear      |

> [!NOTE]
> **Endurance** is measured in **DWPD (Drive Writes Per Day)**. Write-intensive workloads require higher DWPD ratings.

---

# 3.2 — Storage Interfaces Deep Dive

The storage interface determines how a drive connects and communicates with the server.

```mermaid
flowchart TD

    DRIVE[Storage Interfaces]

    DRIVE --> SATA[SATA]
    DRIVE --> SAS[SAS]
    DRIVE --> NVME[NVMe]

    SATA --> S1[Entry / Single Path]
    SAS --> S2[Enterprise / Dual Path]
    NVME --> S3[Direct PCIe Connection]
```

| Interface | Tier        |  Paths | Notes                                  |
| --------- | ----------- | :----: | -------------------------------------- |
| **SATA**  | Entry       | Single | Lower throughput and cost              |
| **SAS**   | Enterprise  |  Dual  | Higher reliability and queue depth     |
| **NVMe**  | Performance |  PCIe  | Lowest latency and highest performance |

> [!TIP]
> SAS dual-path connectivity allows the drive to remain accessible even if one controller path fails.

---

# 3.3 — RAID Levels

**RAID (Redundant Array of Independent Disks)** combines multiple drives to provide:

* Performance
* Redundancy
* Fault tolerance

## Visual Overview

```mermaid
flowchart TB

    subgraph R0[RAID 0 - Striping]
        A0[Disk 1]
        A1[Disk 2]
    end

    subgraph R1[RAID 1 - Mirroring]
        B0[Disk 1]
        B1[Copy of Disk 1]
    end

    subgraph R5[RAID 5 - Parity]
        C0[Disk 1]
        C1[Disk 2]
        C2[Parity]
    end

    subgraph R10[RAID 10 - Mirror + Stripe]
        D0[Mirror Set A]
        D1[Mirror Set B]
    end
```

## RAID Comparison

|  RAID  | Technique         | Min Disks |  Fault Tolerance  | Usable Capacity | Best For                      |
| :----: | ----------------- | :-------: | :---------------: | :-------------: | ----------------------------- |
|  **0** | Striping          |     2     |        None       |       100%      | Temporary data, scratch disks |
|  **1** | Mirroring         |     2     |       1 disk      |       50%       | OS drives, critical data      |
|  **5** | Striping + Parity |     3     |       1 disk      |     (n−1)/n     | Balanced protection           |
|  **6** | Double Parity     |     4     |      2 disks      |     (n−2)/n     | Large drive arrays            |
| **10** | Mirror + Stripe   |     4     | 1 per mirror pair |       50%       | Databases and virtualization  |

> [!WARNING]
> RAID 0 provides no fault tolerance. A single disk failure destroys the entire array.

> [!IMPORTANT]
> RAID is not a backup. RAID protects against disk failures, not accidental deletion, corruption, ransomware, or site disasters.

---

# 3.4 — Controllers, Hot Spare & Hot Swap

## Hardware vs Software RAID

| Aspect           | Hardware RAID        | Software RAID    |
| ---------------- | -------------------- | ---------------- |
| Processing       | Dedicated controller | Operating system |
| Performance      | Cache-assisted       | CPU dependent    |
| Cost             | Higher               | Lower            |
| Cache Protection | Battery/Flash cache  | OS dependent     |

```mermaid
flowchart LR

    OS[Operating System]

    OS --> CTRL[RAID Controller + Cache]

    CTRL --> BP[Backplane]

    BP --> D1[Disk 1]
    BP --> D2[Disk 2]
    BP --> D3[Disk 3]
    BP --> HS[Hot Spare]
```

## Key Operational Concepts

* **Hot Swap** — Replace a failed drive without shutting down the server.
* **Hot Spare** — Standby drive that automatically rebuilds the array.
* **BBWC / FBWC** — Battery-backed or flash-backed write cache protecting cached data.

> [!TIP]
> Combining RAID, hot spares, and hot-swap drive bays enables storage maintenance with little or no downtime.

---

# Day 3 Summary

* **HDD** provides capacity and low cost.
* **SSD** balances performance and price.
* **NVMe** delivers the lowest latency and highest IOPS.
* **SATA** is entry-level storage.
* **SAS** offers enterprise reliability.
* **NVMe** provides direct PCIe performance.
* **RAID** improves performance and redundancy.
* RAID is never a replacement for backups.

---

## Learning Outcomes

* Compare HDD, SSD, and NVMe technologies.
* Select the appropriate RAID level.
* Understand hot swap and hot spare concepts.
* Explain controller cache protection.

---

## Knowledge Check

<details>
<summary>Click to reveal quick quiz questions</summary>

1. Which storage technology provides the highest IOPS?
2. What does DWPD measure?
3. How many drive failures can RAID 6 tolerate?
4. Why is RAID 0 risky?
5. What is the difference between hot swap and hot spare?
6. Why is RAID not considered a backup?

</details>

---

<p align="center">
  <a href="#day-3--storage--raid">Back to Top</a>
  •
  <b>Prev:</b> Day 2 — Core Components
  •
  <b>Next:</b> Day 4 — Performance & Sizing
</p>
