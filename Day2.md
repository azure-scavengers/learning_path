<h1 align="center"> Day 2 — Core Components</h1>
<p align="center">  <img src="https://img.shields.io/badge/Level-Beginner-3fb950?style=for-the-badge" alt="Level: Beginner" />  <img src="https://img.shields.io/badge/Track-Server%20Hardware-1f6feb?style=for-the-badge" alt="Track: Server Hardware" />  <img src="https://img.shields.io/badge/Module-2%20of%207-8957e5?style=for-the-badge" alt="Module 2 of 7" /></p>
<p align="center">  <b>Goal:</b> Identify every major internal component and understand its purpose — CPU, memory, motherboard, power, and the network/storage interfaces that connect a server to the world.</p>
---
## Topics in This Module
1. [CPU (Processor)](#-21--cpu-processor)2. [Memory (RAM)](#-22--memory-ram)3. [Motherboard, Chipset & Buses](#-23--motherboard-chipset--buses)4. [Power Supply Unit (PSU)](#-24--power-supply-unit-psu)5. [Network & Storage Interfaces](#-25--network--storage-interfaces)
---
## 2.1 — CPU (Processor)
The **CPU (Central Processing Unit)** executes instructions — it is the "brain" of the server. Server-class CPUs (Intel **Xeon**, AMD **EPYC**) are built for many cores, large caches, ECC memory support, and multi-socket configurations.
### Key Concepts
| Term | Meaning ||---|---|| **Core** | An independent processing unit; more cores = more parallel work. || **Thread** | A logical execution stream; with SMT/Hyper-Threading one core runs 2 threads. || **Clock Speed (GHz)** | Cycles per second; higher helps single-threaded workloads. || **Cache (L1/L2/L3)** | Small, ultra-fast memory close to the core to reduce latency. || **Socket** | The physical CPU mount; servers may have 1, 2, or more. |
### Single vs Multi-Socket
```mermaidflowchart LR    subgraph Single[Single-Socket]        C1[CPU 0]    end    subgraph Dual[Dual-Socket]        C2[CPU 0]        C3[CPU 1]        C2 <-->|Interconnect| C3    end```
### Server CPU vs Desktop CPU
| Attribute | Desktop CPU | Server CPU ||---|---|---|| Core count | Lower | Very high || ECC memory | Often unsupported | Supported || Sockets | 1 | 1, 2, or more || Reliability features | Basic | Extensive (RAS) |
> [!NOTE]> **More cores vs higher clock** is a trade-off: parallel workloads (virtualization, databases) favor more cores; latency-sensitive single-threaded tasks favor higher clock speed.
---
## 2.2 — Memory (RAM)
**RAM (Random Access Memory)** is fast, volatile working storage for active data and running processes. Servers install memory as **DIMM** modules and almost always use **ECC**.
### Why ECC Matters
```mermaidflowchart LR    DATA[Incoming Data] --> ECC{ECC Check}    ECC -->|No error| OK[Stored / Used]    ECC -->|Single-bit error| FIX[Auto-corrected]    ECC -->|Detected fault| LOG[Logged + Alerted]```
> [!IMPORTANT]> **ECC (Error-Correcting Code)** memory detects and corrects single-bit errors automatically — critical for servers running 24×7 where silent data corruption is unacceptable.
### DIMM Types
| Type | Full Name | Typical Use ||---|---|---|| **UDIMM** | Unbuffered DIMM | Entry-level servers / workstations || **RDIMM** | Registered DIMM | Mainstream servers (better stability & capacity) || **LRDIMM** | Load-Reduced DIMM | Very high-capacity configurations |
### Specs to Know
- **Capacity** (e.g., 16 GB, 32 GB, 64 GB per DIMM)- **Speed** (e.g., DDR4-3200, DDR5-4800 in MHz/MT/s)- **Channels** — balanced DIMM population maximizes bandwidth (covered on Day 4).
---
## 2.3 — Motherboard, Chipset & Buses
The **motherboard (mainboard)** ties every component together and defines the server's expansion limits.
```mermaidflowchart TB    MB[Motherboard]    MB --- SOCK[CPU Socket s]    MB --- DIMM[DIMM Slots]    MB --- CHIP[Chipset]    MB --- PCIE[PCIe Slots / Lanes]    PCIE --- ADDIN[NIC / GPU / RAID / NVMe]    MB --- IO[Onboard I/O + Mgmt]```
### PCIe — The Expansion Backbone
- **PCIe (Peripheral Component Interconnect Express)** connects expansion cards.- Measured in **lanes** (x1, x4, x8, x16) — more lanes = more bandwidth.- **Generations** (Gen3 → Gen4 → Gen5) roughly **double** bandwidth each step.
| PCIe Use | Example Card ||---|---|| Networking | NIC (10/25/100 GbE) || Compute | GPU / AI accelerator || Storage | RAID controller, NVMe |
> [!TIP]> Always check both the **slot count** and the **lane budget** of a motherboard — a slot may be physically x16 but only wired x8.
---
## 2.4 — Power Supply Unit (PSU)
The **PSU** converts incoming **AC** power into the **DC** voltages the server's components need.
```mermaidflowchart LR    AC[AC Mains] --> PSU[PSU]    PSU --> DC1[12V]    PSU --> DC2[5V]    PSU --> DC3[3.3V]    DC1 --> COMP[Server Components]    DC2 --> COMP    DC3 --> COMP```
### Efficiency Ratings — 80 PLUS
| Rating | Relative Efficiency ||---|---|| Bronze | Good || Silver | Better || Gold | High (common in servers) || Platinum | Very high || Titanium | Highest |
### Redundant Power (1+1)
```mermaidflowchart LR    FEED1[Power Feed A] --> PSU1[PSU 1]    FEED2[Power Feed B] --> PSU2[PSU 2]    PSU1 --> SRV[Server]    PSU2 --> SRV```
> [!NOTE]> With **redundant PSUs (1+1)**, the server keeps running if one PSU or one power feed fails. Redundancy is explored further on **Day 5**.
---
## 2.5 — Network & Storage Interfaces
These interfaces connect the server to the **network** and to its **storage**.
### Network Interface (NIC)
| Speed | Common Use ||---|---|| **1 GbE** | Management / legacy || **10 GbE** | Standard server networking || **25 GbE** | Modern data center workloads || **100 GbE** | High-throughput / storage networks |
- **Onboard NIC:** built into the motherboard.- **Add-in NIC:** PCIe card for higher speeds or more ports.
### Storage Interfaces (Preview)
| Interface | Tier | Notes ||---|---|---|| **SATA** | Entry / consumer | Single-path, lower throughput || **SAS** | Enterprise | Dual-path, higher reliability & queue depth || **NVMe** | Performance | Flash over PCIe, lowest latency |
> [!IMPORTANT]> Storage media and interfaces are covered in depth on **Day 3 — Storage & RAID**. Today you only need to recognize the names and their relative tiers.
---
## Day 2 Summary
- The **CPU** executes work; key dimensions are **cores, threads, clock speed, cache, and sockets**.- **RAM (ECC DIMMs)** holds active data; **RDIMM/LRDIMM/UDIMM** suit different capacity needs.- The **motherboard** connects everything; **PCIe lanes** are the expansion backbone for NICs, GPUs, and storage.- The **PSU** converts AC→DC; **80 PLUS** ratings show efficiency and **redundant PSUs** protect uptime.- **NICs** connect to the network (1/10/25/100 GbE); **SATA/SAS/NVMe** connect storage.
### Outcomes- Name and describe the function of CPU, RAM, motherboard, PSU, NIC, and storage interfaces.- Explain why **ECC memory** and **server-grade CPUs** matter.- Read basic PCIe, memory, and power specs.
---
## Knowledge Check
<details><summary>Click to reveal quick-quiz questions</summary>
1. What is the difference between a CPU core and a thread?2. Why do servers use ECC memory?3. What does a PCIe "x8" notation describe?4. Name two benefits of redundant (1+1) power supplies.5. Rank SATA, SAS, and NVMe from lowest to highest performance.6. When would you choose more cores over a higher clock speed?
</details>
---
<p align="center">  <a href="#-day-2--core-components"> Back to top</a> &nbsp;•&nbsp; <b>Prev:</b> Day 1 — Server Basics &nbsp;•&nbsp; <b>Next:</b> Day 3 — Storage & RAID</p>
