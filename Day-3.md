<h1 align="center"> Day 3 — Storage & RAID</h1>
<p align="center">  <img src="https://img.shields.io/badge/Level-Intermediate-d29922?style=for-the-badge" alt="Level: Intermediate" />  <img src="https://img.shields.io/badge/Track-Server%20Hardware-1f6feb?style=for-the-badge" alt="Track: Server Hardware" />  <img src="https://img.shields.io/badge/Module-3%20of%207-8957e5?style=for-the-badge" alt="Module 3 of 7" /></p>
<p align="center">  <b>Goal:</b> Understand storage media types, how they connect, and how RAID delivers performance and redundancy.</p>
---
## Topics in This Module
1. [Storage Media Types](#-31--storage-media-types)2. [Storage Interfaces Deep Dive](#-32--storage-interfaces-deep-dive)3. [RAID Levels](#-33--raid-levels)4. [Controllers, Hot Spare & Hot Swap](#-34--controllers-hot-spare--hot-swap)
---
## 3.1 — Storage Media Types
Servers choose storage media by balancing **cost, capacity, speed, and endurance**.
```mermaidflowchart LR    HDD[HDD - Spinning Disk] --> CAP[High Capacity / Low Cost]    SSD[SSD - Flash] --> BAL[Balanced Speed]    NVME[NVMe - Flash over PCIe] --> FAST[Lowest Latency / Highest IOPS]```
| Media | Speed | Cost / GB | Best For | Failure Risk ||---|:---:|:---:|---|---|| **HDD** | Low | Lowest | Bulk / archival / backups | Mechanical wear || **SSD (SATA/SAS)** | High | Medium | General-purpose workloads | Flash wear || **NVMe** | Very High | Higher | Databases, high-IOPS, caching | Flash wear |
> [!NOTE]> **Endurance** is measured in **DWPD** (Drive Writes Per Day) — how many times the full drive can be overwritten daily over its warranty. Write-heavy workloads need higher DWPD drives.
---
## 3.2 — Storage Interfaces Deep Dive
The **interface** determines how a drive connects and how fast/reliably it talks to the server.
```mermaidflowchart TD    DRIVE[Storage Interfaces]    DRIVE --> SATA[SATA]    DRIVE --> SAS[SAS]    DRIVE --> NVME[NVMe]    SATA --> S1[Entry / single-path]    SAS --> S2[Enterprise / dual-path]    NVME --> S3[Direct PCIe connection]```
| Interface | Tier | Paths | Notes ||---|---|:---:|---|| **SATA** | Entry / consumer | Single | Lower throughput, lower cost || **SAS** | Enterprise | Dual | Higher reliability, deeper queue depth || **NVMe** | Performance | PCIe | Lowest latency; U.2 / M.2 / EDSFF form factors |
> [!TIP]> **SAS dual-path** means a drive can stay reachable even if one path fails — a key enterprise reliability advantage over SATA.
---
## 3.3 — RAID Levels
**RAID (Redundant Array of Independent Disks)** combines multiple drives for **performance**, **redundancy**, or both.
### Visual Overview
```mermaidflowchart TB    subgraph R0[RAID 0 - Striping]        A0[Disk 1]         A1[Disk 2]    end    subgraph R1[RAID 1 - Mirroring]        B0[Disk 1]        B1[Copy of Disk 1]    end    subgraph R5[RAID 5 - Stripe + Parity]        C0[Disk 1]        C1[Disk 2]        C2[Parity]    end    subgraph R10[RAID 10 - Mirror + Stripe]        D0[Mirror A]        D1[Mirror B]    end```
### Comparison
| RAID | Technique | Min Disks | Fault Tolerance | Usable Capacity | Best For ||:---:|---|:---:|:---:|:---:|---|| **0** | Striping | 2 | None | 100% | Pure speed (scratch/temp only) || **1** | Mirroring | 2 | 1 disk | 50% | OS drives, small critical data || **5** | Stripe + parity | 3 | 1 disk | (n-1)/n | Balanced capacity + protection || **6** | Stripe + double parity | 4 | 2 disks | (n-2)/n | Large arrays, big drives || **10** | Mirror + stripe | 4 | 1 per mirror | 50% | High performance + redundancy (databases) |
> [!WARNING]> **RAID 0 has no redundancy.** A single disk failure destroys the entire array. Never use it for data you cannot afford to lose.
> [!IMPORTANT]> **RAID is not a backup.** It protects against *drive failure*, not against deletion, corruption, ransomware, or site loss. Always keep separate backups.
---
## 3.4 — Controllers, Hot Spare & Hot Swap
### Hardware vs Software RAID
| Aspect | Hardware RAID | Software RAID ||---|---|---|| Where it runs | Dedicated controller card | OS / CPU || Performance | Offloaded, cache-backed | Uses host CPU || Cost | Higher | Lower || Cache protection | Battery / flash-backed write cache | Depends on OS |
```mermaidflowchart LR    OS[Operating System] --> CTRL[RAID Controller + Cache]    CTRL --> BP[Backplane]    BP --> D1[Disk 1]    BP --> D2[Disk 2]    BP --> D3[Disk 3]    BP --> HS[Hot Spare]```
### Key Operational Concepts
- **Hot Swap** — replace a failed drive **while the server is running**, no shutdown needed.- **Hot Spare** — a standby drive that **auto-rebuilds** the array when a member fails.- **Battery/Flash-Backed Write Cache (BBWC/FBWC)** — protects in-flight cached writes during a power loss.
> [!TIP]> Pair **RAID redundancy + a hot spare + hot-swap bays** so a failed disk can be replaced and rebuilt with zero downtime.
---
## Day 3 Summary
- Pick media by trade-off: **HDD** (capacity/cost), **SSD** (balanced), **NVMe** (lowest latency / highest IOPS).- Interfaces: **SATA** (entry), **SAS** (enterprise dual-path), **NVMe** (PCIe performance).- **RAID** provides speed and/or redundancy — **0** (speed, no safety), **1** (mirror), **5** (single parity), **6** (double parity), **10** (mirror+stripe).- **RAID is not a backup**; combine it with **hot spare** + **hot-swap** + cache protection for resilient storage.
### Outcomes- Compare HDD, SSD, and NVMe and select appropriately.- Choose the correct RAID level for a given workload and risk profile.- Explain hot swap, hot spare, and controller cache protection.
---
## Knowledge Check
<details><summary>Click to reveal quick-quiz questions</summary>
1. Which media type gives the highest IOPS and lowest latency?2. What does DWPD measure?3. How many disk failures can RAID 6 tolerate?4. Why is RAID 0 unsafe for important data?5. What is the difference between a hot spare and a hot swap?6. Why is "RAID is not a backup" an important rule?
</details>
---
<p align="center">  <a href="#-day-3--storage--raid"> Back to top</a> &nbsp;•&nbsp; <b>Prev:</b> Day 2 — Core Components &nbsp;•&nbsp; <b>Next:</b> Day 4 — Performance & Sizing</p>
