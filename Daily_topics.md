# Server Hardware Training Program
## Overview
This 7-day training plan is designed for new joiners, moving from **beginner fundamentals** to **expert-level decision-making** in server hardware.
- **Total class time:** 12 hours (max)- **Audience:** Freshers, junior engineers, IT support, platform trainees- **Goal:** Build practical confidence in selecting, operating, troubleshooting, and scaling server hardware
---
## Schedule at a Glance
| Day | Duration | Level | Module ||---|---:|---|---|| 1 | 1.5h | Beginner | Server Basics || 2 | 1.5h | Beginner | Core Components || 3 | 1.5h | Intermediate | Storage & RAID || 4 | 1.5h | Intermediate | Performance & Sizing || 5 | 2.0h | Advanced | Reliability & Operations || 6 | 2.0h | Advanced | Security & Compliance || 7 | 2.0h | Expert | Architecture & Cost Optimization |
**Total = 12 hours**
---
# Day 1 — Server Basics (Beginner, 1.5h)
**Objective:** Understand what a server is, how it differs from a desktop, and recognize the major physical form factors.
### Topic 1.1 — What Is a Server (20 min)- Definition: a computer dedicated to providing services (compute, storage, applications) to other machines (clients) over a network.- Server vs desktop: built for 24x7 uptime, redundancy, remote management, and higher I/O, not for a single interactive user.- Common server roles: web server, database server, file server, application server, virtualization host, domain controller.- Client-server model: how requests and responses flow between users and servers.
### Topic 1.2 — Server Form Factors (30 min)- **Tower servers:** look like desktops, good for small offices, low density, easy to cool, limited scalability.- **Rack servers:** mounted in a 19-inch rack, measured in "U" (1U = 1.75 inches). Dense, standardized, the most common enterprise choice.- **Blade servers:** thin modular boards sharing a common chassis (power, cooling, networking). High density, lower cabling, higher upfront cost.- **Rack units, depth, and weight:** how to read 1U/2U/4U specs and plan rack space.
### Topic 1.3 — On-Prem vs Cloud Hardware View (20 min)- On-premises: you own and operate the physical hardware in your own data center.- Cloud/IaaS: hardware is abstracted; you rent virtual machines but the same hardware concepts (CPU, RAM, storage, network) still apply underneath.- Hybrid: mix of both; why hardware literacy matters even in cloud-first teams.
### Hands-on / Activity (20 min)- Identify hardware parts from sample diagrams and photos.- Match each form factor to a business scenario (small office, enterprise data center, high-density compute).
### Day 1 Outcomes- Explain what a server does and how it differs from a desktop.- Identify tower, rack, and blade servers and when to use each.
---
# Day 2 — Core Components (Beginner, 1.5h)
**Objective:** Identify every major internal component and understand its purpose.
### Topic 2.1 — CPU (Processor) (20 min)- Role: executes instructions; the "brain" of the server.- Key terms: cores, threads, clock speed (GHz), cache (L1/L2/L3), sockets.- Server CPUs vs desktop CPUs: more cores, ECC support, multi-socket capability (e.g., Intel Xeon, AMD EPYC).- Single-socket vs dual-socket vs multi-socket designs.
### Topic 2.2 — Memory (RAM) (20 min)- Role: fast temporary storage for active data and running processes.- DIMM modules, capacity, and speed (MHz).- **ECC (Error-Correcting Code) memory:** detects and corrects memory errors, critical for servers.- Registered (RDIMM) vs Load-Reduced (LRDIMM) vs Unbuffered (UDIMM).
### Topic 2.3 — Motherboard, Chipset & Buses (15 min)- Motherboard ties all components together.- PCIe slots and lanes: how expansion cards (NICs, GPUs, RAID controllers) connect.- Chipset role and expansion limits.
### Topic 2.4 — Power Supply Unit (PSU) (15 min)- Converts AC to DC for components.- Wattage sizing and efficiency ratings (80 PLUS Bronze/Silver/Gold/Platinum/Titanium).- Introduction to redundant PSUs (covered deeper on Day 5).
### Topic 2.5 — Network Interface & Storage Interfaces (10 min)- NIC: 1GbE, 10GbE, 25GbE and beyond; onboard vs add-in cards.- Storage interfaces overview: SATA, SAS, NVMe (detailed on Day 3).
### Hands-on / Activity (10 min)- Component matching exercise: match each part to its function and a real product example.
### Day 2 Outcomes- Name and describe the function of CPU, RAM, motherboard, PSU, NIC, and storage interfaces.- Explain why ECC memory and server-grade CPUs matter.
---
# Day 3 — Storage & RAID (Intermediate, 1.5h)
**Objective:** Understand storage media types and how RAID provides performance and redundancy.
### Topic 3.1 — Storage Media Types (25 min)- **HDD:** spinning disks, high capacity, low cost per GB, slower, mechanical failure risk.- **SSD (SATA/SAS):** flash-based, much faster, no moving parts, higher cost per GB.- **NVMe:** flash over PCIe, lowest latency and highest throughput; ideal for databases and high-IOPS workloads.- Comparing cost, capacity, speed, and endurance (DWPD - drive writes per day).
### Topic 3.2 — Storage Interfaces Deep Dive (15 min)- SATA: consumer/entry, single-path, lower throughput.- SAS: enterprise, dual-path, higher reliability and queue depth.- NVMe: direct PCIe connection, U.2/M.2/EDSFF form factors.
### Topic 3.3 — RAID Levels (35 min)- **RAID 0 (striping):** speed, no redundancy; one disk failure loses all data.- **RAID 1 (mirroring):** full redundancy, 50% usable capacity.- **RAID 5 (striping + parity):** one disk fault tolerance, good capacity efficiency.- **RAID 6 (double parity):** two disk fault tolerance, better for large arrays.- **RAID 10 (1+0):** mirror + stripe, high performance and redundancy, 50% usable capacity.- Hardware RAID vs software RAID; RAID controllers and battery/flash-backed write cache.- Hot spare and hot swap concepts.
### Hands-on / Activity (10 min)- RAID design scenarios: pick the right RAID level for given capacity, performance, and fault-tolerance requirements.
### Day 3 Outcomes- Compare HDD, SSD, and NVMe and select appropriately.- Choose the correct RAID level for a given workload and risk profile.
---
# Day 4 — Performance & Sizing (Intermediate, 1.5h)
**Objective:** Translate workload requirements into a balanced hardware specification.
### Topic 4.1 — CPU Sizing (20 min)- Cores vs threads and how workloads use them.- Clock speed vs core count trade-offs (single-threaded vs parallel workloads).- NUMA (Non-Uniform Memory Access) basics in multi-socket systems.
### Topic 4.2 — Memory Sizing (20 min)- Capacity planning: OS + application + cache + headroom.- Memory channels and balanced DIMM population for maximum bandwidth.- Impact of insufficient RAM (swapping/paging) on performance.
### Topic 4.3 — Storage Performance (20 min)- **IOPS, throughput (MB/s), and latency** explained.- Matching media (HDD/SSD/NVMe) to IOPS requirements.- Queue depth and how RAID level affects performance.
### Topic 4.4 — Bottleneck Analysis (15 min)- The weakest link principle: CPU, memory, storage, or network can each be the bottleneck.- How to read basic utilization metrics to find the constraint.- Balanced design vs over-provisioning.
### Hands-on / Activity (15 min)- Sizing worksheet for common workloads (web server, database, file server, virtualization host).
### Day 4 Outcomes- Size CPU, memory, and storage for a given workload.- Identify likely bottlenecks and design a balanced configuration.
---
# Day 5 — Reliability & Operations (Advanced, 2.0h)
**Objective:** Build for uptime and learn how servers are managed and monitored in production.
### Topic 5.1 — Redundancy (30 min)- Redundant PSUs (1+1) and dual power feeds.- Redundant NICs: NIC teaming/bonding and failover.- Redundant fans and N+1 cooling.- Single point of failure (SPOF) identification and elimination.
### Topic 5.2 — Thermal & Power Design (20 min)- Airflow (front-to-back), hot aisle / cold aisle data center layout.- Operating temperature ranges and thermal throttling.- Power draw, PDU capacity, and UPS basics.
### Topic 5.3 — Firmware & Out-of-Band Management (35 min)- BIOS/UEFI: boot configuration, settings, and updates.- Baseboard Management Controller (BMC): the foundation of remote management.- **iDRAC (Dell), iLO (HPE), IPMI:** remote console, power control, health, and virtual media.- Firmware update strategy and why it matters for security and stability.
### Topic 5.4 — Monitoring Essentials (20 min)- Health indicators: temperature, fan speed, PSU status, disk health (SMART).- Hardware logs and alerting (SNMP, Redfish API).- Predictive failure alerts and proactive replacement.
### Hands-on / Activity (15 min)- Failure-mode drill: walk through PSU failure, disk failure, and NIC failure response steps.
### Day 5 Outcomes- Design redundancy to eliminate single points of failure.- Use out-of-band management tools and interpret hardware health data.
---
# Day 6 — Security & Compliance (Advanced, 2.0h)
**Objective:** Secure server hardware across its lifecycle and meet compliance expectations.
### Topic 6.1 — Boot & Platform Security (30 min)- **Secure Boot:** ensures only trusted, signed firmware/OS loads.- **TPM (Trusted Platform Module):** hardware root of trust, key storage, disk encryption support.- UEFI security settings and firmware passwords.
### Topic 6.2 — Firmware & Supply Chain Hardening (30 min)- Firmware vulnerabilities and patch discipline.- Signed firmware and verified update channels.- Supply chain risk: tampering, counterfeit components, and trusted vendors.
### Topic 6.3 — Physical Security (20 min)- Data center access control, cabinet locks, and bezels.- Chassis intrusion detection.- Asset tagging and tracking.
### Topic 6.4 — Hardware Lifecycle Governance (25 min)- Procurement, deployment, maintenance, and decommissioning.- **Secure data destruction:** drive wiping, cryptographic erase, and physical shredding.- Compliance frameworks awareness (e.g., data residency, audit requirements).- Warranty and support contract management.
### Hands-on / Activity (15 min)- Hardening checklist walkthrough applied to a sample server build.
### Day 6 Outcomes- Apply boot, firmware, and physical security controls.- Manage hardware securely from procurement to decommissioning.
---
# Day 7 — Architecture & Cost Optimization (Expert, 2.0h)
**Objective:** Make strategic hardware decisions balancing performance, reliability, and cost.
### Topic 7.1 — Build vs Buy & Refresh Strategy (25 min)- Owning hardware vs leasing vs cloud consumption.- Hardware refresh cycles (typically 3 to 5 years) and why.- End-of-life and end-of-support planning.
### Topic 7.2 — Workload Placement (25 min)- Matching workloads to hardware (compute-optimized, memory-optimized, storage-optimized).- Virtualization and consolidation: more workloads per physical server.- When to scale up (bigger server) vs scale out (more servers).
### Topic 7.3 — Total Cost of Ownership (TCO) (30 min)- CapEx vs OpEx.- TCO components: hardware, power, cooling, space, support, and staff.- Power efficiency and density as cost drivers.- Cost-performance trade-off analysis.
### Topic 7.4 — Capacity Planning (20 min)- Forecasting growth and headroom planning.- Avoiding over-provisioning and under-provisioning.- Aligning capacity with business demand.
### Capstone (20 min)- Present and review the capstone hardware architecture (see prompt below).
### Day 7 Outcomes- Recommend a hardware architecture with justified cost-performance trade-offs.- Plan refresh cycles, workload placement, and capacity growth.
---
## Module Outcomes (Overall)
By the end of the program, participants will be able to:
1. Explain server hardware fundamentals clearly.2. Choose suitable hardware configurations for common workloads.3. Apply reliability and security best practices.4. Diagnose basic performance and hardware issues.5. Present a justified architecture recommendation with cost-performance trade-offs.
---
## Delivery Format
- **Session model:** 60% instructor-led, 40% practical discussion/labs- **Daily flow:** recap (10 min), core module, activity/lab, Q&A- **Suggested batch size:** 15 to 25 learners
---
## Assessment Plan
- **Daily quick quiz:** 5 to 8 questions- **Scenario-based tasks:** Days 3 to 6- **Final capstone review:** Day 7- **Completion criteria:** 70%+ score + capstone participation
---
## Materials Checklist
- Slide deck per day- Component reference sheet (CPU/RAM/storage/network)- RAID and sizing cheat sheets- Monitoring and hardening checklists- Capstone template (requirements, assumptions, recommendation, risks)
---
## Glossary (Quick Reference)
| Term | Meaning ||---|---|| U (Rack Unit) | 1.75 inches of vertical rack space || ECC | Error-Correcting Code memory || RDIMM/LRDIMM | Registered / Load-Reduced memory modules || PCIe | Peripheral Component Interconnect Express expansion bus || SAS/SATA/NVMe | Storage interface types (enterprise / consumer / PCIe flash) || RAID | Redundant Array of Independent Disks || IOPS | Input/Output Operations Per Second || NUMA | Non-Uniform Memory Access || BMC | Baseboard Management Controller || iDRAC/iLO/IPMI | Out-of-band remote management interfaces || TPM | Trusted Platform Module || SPOF | Single Point of Failure || TCO | Total Cost of Ownership || CapEx/OpEx | Capital / Operational Expenditure |
---
## Suggested Capstone Prompt
Design server hardware for a mid-size enterprise app stack:- Web tier, API tier, database tier- High availability required- 20% yearly growth expected- Budget-constrained, but no single point of failure allowed
Deliverables:- Proposed hardware spec- Redundancy plan- Security controls- Cost and scalability rationale
