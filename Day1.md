# Day 1 — Server Basics
> **Module Level:** Beginner &nbsp;|&nbsp; **Duration:** 1.5 hours &nbsp;|&nbsp; **Track:** Server Hardware Training
---
## At a Glance
| # | Topic | Time | Focus ||---|---|---:|---|| 1.1 | What Is a Server | 20 min | Concept & roles || 1.2 | Server Form Factors | 30 min | Tower / Rack / Blade || 1.3 | On-Prem vs Cloud Hardware View | 15 min | Where hardware lives || 1.4 | Inside the Server: Hardware Components | 25 min | Tour of internal parts |
**Objective:** Understand what a server is, how it differs from a desktop, and recognize the major physical form factors.
---
## Topic 1.1 — What Is a Server (20 min)
A **server** is a computer dedicated to providing services (compute, storage, applications) to other machines called **clients**, usually over a network. Unlike a desktop built for one interactive user, a server is built for **24x7 uptime, redundancy, remote management, and high I/O**.
### The Client-Server Model
```mermaidflowchart LR    C1[Client - Laptop]    C2[Client - Phone]    C3[Client - Desktop]    NET((Network))    SRV[Server]    C1 -->|Request| NET    C2 -->|Request| NET    C3 -->|Request| NET    NET --> SRV    SRV -->|Response| NET```
### Server vs Desktop
| Attribute | Desktop | Server ||---|---|---|| Uptime | Working hours | 24x7 || Users | Single | Many (clients) || Memory | Standard | ECC (error-correcting) || Power supply | Single | Often redundant || Management | Local | Remote / out-of-band |
### Common Server Roles
```mermaidmindmap  root((Server Roles))    Web Server    Database Server    File Server    Application Server    Virtualization Host    Domain Controller```
> **Image placeholder:** `assets/server-hardware/day1-datacenter.jpg` — a photo of a real data center rack row.
---
## Topic 1.2 — Server Form Factors (30 min)
The three main physical formats. Each trades off **density, scalability, cost, and cooling**.
```mermaidflowchart TD    F[Server Form Factors]    F --> T[Tower]    F --> R[Rack]    F --> B[Blade]    T --> T1[Looks like a desktop]    T --> T2[Small office, low density]    R --> R1[19-inch rack mounted]    R --> R2[Measured in U - 1U = 1.75 in]    B --> B1[Modular blades in a chassis]    B --> B2[Shared power, cooling, network]```
### Comparison
| Form Factor | Density | Scalability | Cost | Best For ||---|---|---|---|---|| **Tower** | Low | Low | Low | Small office, single server || **Rack** | Medium-High | High | Medium | Enterprise data centers || **Blade** | Very High | Very High | High upfront | High-density compute |
### Understanding Rack Units (U)
A rack is **19 inches** wide and measured vertically in **U**, where **1U = 1.75 inches**.
```mermaidflowchart TB    subgraph RACK[19-inch Rack]        direction TB        U42[42U ... top]        S2[2U Server]        S1[1U Server]        U1[1U ... bottom]    end```
> **Image placeholder:** `assets/server-hardware/day1-formfactors.png` — side-by-side tower, rack, and blade photos.
---
## Topic 1.3 — On-Prem vs Cloud Hardware View (15 min)
Even in cloud-first teams, the same hardware concepts (CPU, RAM, storage, network) exist underneath the abstraction.
```mermaidflowchart LR    subgraph OnPrem[On-Premises]        A[You own the hardware]        B[Your data center]    end    subgraph Cloud[Cloud / IaaS]        C[Rent virtual machines]        D[Provider owns hardware]    end    subgraph Hybrid[Hybrid]        E[Mix of both]    end    OnPrem --- Hybrid --- Cloud```
| Model | Who Owns Hardware | You Manage | Hardware Literacy Needed? ||---|---|---|---|| On-Prem | You | Everything | Yes || Cloud (IaaS) | Provider | OS & apps | Yes (it still maps to real hardware) || Hybrid | Both | Shared | Yes |
> **Key takeaway:** A cloud VM with "8 vCPU, 32 GB RAM, SSD" maps directly to the physical CPU, memory, and storage concepts covered in this course.
---
## Topic 1.4 — Inside the Server: Hardware Components (25 min)
Open a rack server and you will find a set of well-organized components. This is a **first-look tour** — each part is studied in depth on later days, but a new joiner should be able to recognize every item on sight.
### Internal Layout (Front to Back)
```mermaidflowchart LR    subgraph CHASSIS[Rack Server Chassis]        direction LR        FRONT[Front: Hot-swap Drive Bays + Backplane]        MID[Middle: Fans + CPU + Memory + Motherboard]        REAR[Rear: PSUs + PCIe Slots + I/O + Mgmt Port]    end    FRONT --> MID --> REAR```
### Component Reference
| Component | What It Is | Why It Matters ||---|---|---|| **CPU (Processor)** | The "brain" that executes instructions; server CPUs (Xeon, EPYC) have many cores and support multiple sockets. | Drives compute power; more cores = more parallel work. || **Memory (RAM / DIMMs)** | Fast temporary working storage installed in DIMM slots; servers use ECC memory. | Holds active data; too little causes slow paging. || **Motherboard / Mainboard** | The board connecting all components together via buses. | Defines socket count, slot count, and expansion limits. || **Control Plane (BMC / Management Controller)** | A separate always-on micro-controller (iDRAC/iLO/IPMI) that manages and monitors the server even when it is powered off. | Enables remote power, console, and health monitoring. || **Hard Disk / Drives (HDD, SSD, NVMe)** | Persistent storage media in hot-swap bays. | Where the OS and data live; type affects speed. || **Backplane** | A board behind the drive bays that connects all drives to the controller without individual cables. | Enables hot-swap and clean drive connectivity. || **Storage / RAID Controller** | Card that manages drives and RAID arrays, often with cache. | Provides redundancy and performance for storage. || **PCIe Slots** | Expansion slots (lanes) for add-in cards. | Add NICs, GPUs, RAID, NVMe, and accelerators. || **Riser Card** | A board that lets PCIe cards mount horizontally in thin chassis. | Allows full-size cards in low-profile servers. || **NIC (Network Interface)** | 1/10/25/100 GbE ports, onboard or add-in. | Connects the server to the network. || **GPU / Accelerator Cards** | High-throughput cards for AI, ML, rendering, and HPC. | Massive parallel compute beyond the CPU. || **VGA / Video Output** | Basic onboard graphics (often via the BMC) for console access. | Local "crash cart" and BIOS access — not for gaming. || **Power Supplies (PSU)** | Convert AC to DC; usually redundant (1+1). | Keep the server running if one PSU fails. || **Cooling Fans** | High-RPM fans pushing front-to-back airflow. | Prevent thermal throttling and component damage. || **TPM Module** | Hardware security chip for keys and secure boot. | Root of trust for platform security. |
### How the Pieces Connect
```mermaidflowchart TB    MB[Motherboard]    CPU[CPU Sockets] --- MB    RAM[Memory DIMMs] --- MB    MB --- PCIE[PCIe Slots / Risers]    PCIE --- NIC[NIC]    PCIE --- GPU[GPU / Accelerator]    PCIE --- RAID[RAID Controller]    RAID --- BP[Backplane]    BP --- DRV[Hot-swap Drives]    MB --- BMC[Control Plane / BMC]    BMC --- VGA[VGA / Remote Console]    PSU[Redundant PSUs] --- MB    FAN[Cooling Fans] --- MB```
### Data Plane vs Control Plane (Quick Concept)
- **Data plane:** the components doing the actual work — CPU, memory, drives, NICs moving real workload traffic.- **Control plane (BMC):** the independent management layer that monitors and controls the server (power, health, firmware, remote console) regardless of the OS state.
> **Image placeholder:** `assets/server-hardware/day1-internal-layout.png` — top-down photo of an open 2U server with parts labeled (CPU, DIMMs, PCIe risers, backplane, PSUs, fans).
---
## Day 1 Summary
- A **server** provides services to clients and is built for uptime, redundancy, and remote management.- The three **form factors** are **tower** (small office), **rack** (enterprise standard, measured in U), and **blade** (high density, shared chassis).- Hardware concepts apply **on-prem and in the cloud** — a cloud VM still maps to real CPU, RAM, storage, and network.- Inside a server, the key parts are the **CPU, memory, motherboard, control plane (BMC), drives, backplane, RAID controller, PCIe slots/risers, NIC, GPU, VGA, PSUs, fans, and TPM**.- The **data plane** does the work; the **control plane (BMC)** manages and monitors the server independently of the OS.
### Outcomes- Explain what a server does and how it differs from a desktop.- Identify tower, rack, and blade servers and when to use each.- Recognize the major internal hardware components on sight and describe each one's purpose.- Distinguish the data plane from the control plane (BMC).
### Quick Quiz1. What is the main difference between a server and a desktop?2. How many inches is 1U?3. What does the backplane connect, and why does it enable hot-swap?4. What is the control plane (BMC) and why can it work when the OS is off?5. Name two types of cards that plug into PCIe slots.6. Why is ECC memory used in servers?
---
## Image Guide (How to Add Photos)
This document uses **Mermaid diagrams** that render automatically in GitHub and VS Code (with the Markdown Preview Mermaid extension). For real photos, drop files into an `assets/server-hardware/` folder and the placeholders above will display them.
Suggested images to source:- `day1-datacenter.jpg` — data center rack row- `day1-formfactors.png` — tower vs rack vs blade- `day1-internal-layout.png` — open server with labeled internal components (CPU, DIMMs, risers, backplane, PSUs, fans)
> **Next:** Day 2 — Core Components (CPU, RAM, motherboard, PSU, NIC, storage interfaces).
