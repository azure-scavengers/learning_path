# Server Hardware Interview & Knowledge Summary

<p align="center">
  <img src="https://img.shields.io/badge/Level-Beginner_to_Intermediate-3fb950?style=for-the-badge" alt="Level">
  <img src="https://img.shields.io/badge/Track-Server%20Hardware-1f6feb?style=for-the-badge" alt="Track">
  <img src="https://img.shields.io/badge/Purpose-Interview%20Preparation-8957e5?style=for-the-badge" alt="Purpose">
</p>

<p align="center">
  <b>Objective:</b> Review the essential server hardware concepts, troubleshooting scenarios, storage technologies, networking fundamentals, and operating system basics commonly asked during interviews.
</p>

---

## Table of Contents

* [1. Basic Hardware Fundamentals](#1-basic-hardware-fundamentals)
* [2. Server-Specific Concepts](#2-server-specific-concepts)
* [3. Storage & Disk Concepts](#3-storage--disk-concepts)
* [4. Networking Basics](#4-networking-basics-hardware-perspective)
* [5. Troubleshooting Scenarios](#5-troubleshooting-scenarios)
* [6. Operating System Awareness](#6-operating-system-awareness)

---

# 1. Basic Hardware Fundamentals

> [!NOTE]
> These concepts form the foundation of all server hardware knowledge.

## Topics

* What are the main components of a server?
* Difference between RAM and ROM.
* What is a CPU?
* What are the key components of a CPU?
* What is cache memory and why is it important?
* Difference between HDD, SSD, and NVMe.
* What is a motherboard?
* What is BIOS / UEFI?

### Key Areas

| Topic       | Importance              |
| ----------- | ----------------------- |
| CPU         | Processing power        |
| RAM         | Active memory           |
| Storage     | Data persistence        |
| Motherboard | Component connectivity  |
| BIOS/UEFI   | Hardware initialization |
| Cache       | CPU performance         |

---

# 2. Server-Specific Concepts

> [!IMPORTANT]
> Servers are designed for reliability, redundancy, and continuous operation.

## Topics

* What is a server?
* How is a server different from a desktop?
* Types of servers.
* RAID concepts.
* Rack servers vs blade servers.
* Server redundancy.
* Hot-swappable components.

### Common Server Types

| Server Type           | Purpose           |
| --------------------- | ----------------- |
| Web Server            | Hosts websites    |
| Database Server       | Stores databases  |
| File Server           | File sharing      |
| Application Server    | Runs applications |
| Mail Server           | Email services    |
| Virtualization Server | Hosts VMs         |

---

# 3. Storage & Disk Concepts

> [!TIP]
> Storage technologies directly affect server performance and reliability.

## Topics

* SAS vs SATA.
* SCSI concepts.
* Disk partitioning.
* RAID failure scenarios.
* Failed disk identification.

### Storage Comparison

| Technology | Performance | Reliability | Typical Use           |
| ---------- | ----------- | ----------- | --------------------- |
| SATA       | Moderate    | Standard    | Entry-level           |
| SAS        | High        | Enterprise  | Servers               |
| NVMe       | Very High   | High        | Performance workloads |

---

# 4. Networking Basics (Hardware Perspective)

> [!NOTE]
> Every server requires network connectivity to communicate with users and services.

## Topics

* What is a NIC?
* Difference between LAN and WAN.
* What is an IP address?
* Switch vs router.
* MAC address concepts.

### Networking Components

| Component   | Purpose              |
| ----------- | -------------------- |
| NIC         | Network connectivity |
| Switch      | Connects devices     |
| Router      | Connects networks    |
| IP Address  | Logical addressing   |
| MAC Address | Physical addressing  |

---

# 5. Troubleshooting Scenarios

> [!WARNING]
> Troubleshooting skills are often more important than theoretical knowledge during interviews.

## Common Scenarios

### Server is Not Powering On

* Check power cables.
* Verify PSU status.
* Check power outlets.
* Inspect motherboard LEDs.
* Test redundant PSUs.

### Server Performance is Slow

* High CPU usage.
* Low memory.
* Disk bottlenecks.
* Network congestion.
* Hardware failures.

### RAID Disk Failure

* Identify failed drive.
* Verify RAID status.
* Replace failed disk.
* Monitor rebuild progress.

### No Display Issue

* Check VGA/monitor.
* Verify cables.
* Inspect GPU.
* Access remote management.
* Reset BIOS if necessary.

### Server Overheating

* Check fan operation.
* Clean dust filters.
* Verify airflow.
* Monitor temperature sensors.
* Replace failed cooling components.

---

# 6. Operating System Awareness

> [!IMPORTANT]
> Hardware administrators often require basic operating system knowledge.

## Topics

* Operating systems used.
* Linux commands.
* Windows commands.
* Device Manager.
* Device drivers.

### Common Commands

| Windows    | Linux   |
| ---------- | ------- |
| ipconfig   | ip addr |
| ping       | ping    |
| tasklist   | ps      |
| netstat    | netstat |
| systeminfo | uname   |

---

# Interview Preparation Checklist

* [ ] Understand CPU and memory concepts.
* [ ] Learn RAID levels.
* [ ] Understand server types.
* [ ] Know storage technologies.
* [ ] Review networking basics.
* [ ] Practice troubleshooting scenarios.
* [ ] Learn basic Windows commands.
* [ ] Learn basic Linux commands.

---

## Quick Self-Assessment

<details>
<summary>Click to expand interview questions</summary>

1. What is the difference between RAM and ROM?
2. Why is ECC memory important?
3. Explain RAID 5.
4. What is hot-swappable hardware?
5. What is the difference between SAS and SATA?
6. What is a MAC address?
7. How do you troubleshoot a server that won't power on?
8. What is Device Manager?
9. What is a driver?
10. What operating systems have you used?

</details>

---

## Final Takeaway

> Successful server administrators combine:
>
> * Hardware knowledge
> * Storage concepts
> * Networking fundamentals
> * Troubleshooting skills
> * Operating system awareness

---

<p align="center">
  <b>Server Hardware Training Series</b><br>
  Day 1 → Basics • Day 2 → Core Components • Day 3 → Storage & RAID
</p>
