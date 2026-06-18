# Day 1 — Server Basics

> **Module Level:** Beginner | **Track:** Server Hardware Training

---

## At a Glance

| # | Topic | Focus |
|---|---|---|
| 1.1 | What Is a Server | Concept & roles |
| 1.2 | Server Form Factors | Tower / Rack / Blade |
| 1.3 | On-Prem vs Cloud Hardware View | Where hardware lives |
| 1.4 | Inside the Server: Hardware Components | Tour of internal parts |

**Objective:** Understand what a server is, how it differs from a desktop, and recognize the major physical form factors.

---

## Topic 1.1 — What Is a Server

A **server** is a computer dedicated to providing services (compute, storage, applications) to other machines called **clients**, usually over a network.

Unlike a desktop built for one interactive user, a server is built for:

- 24×7 uptime
- Redundancy
- Remote management
- High I/O

### The Client-Server Model

```mermaid
flowchart LR
    C1[Client - Laptop]
    C2[Client - Phone]
    C3[Client - Desktop]
    NET((Network))
    SRV[Server]

    C1 -->|Request| NET
    C2 -->|Request| NET
    C3 -->|Request| NET

    NET --> SRV
    SRV -->|Response| NET
```

### Server vs Desktop

| Attribute | Desktop | Server |
|------------|----------|----------|
| Uptime | Working hours | 24x7 |
| Users | Single | Many (clients) |
| Memory | Standard | ECC (error-correcting) |
| Power Supply | Single | Often redundant |
| Management | Local | Remote / Out-of-band |

### Common Server Roles

```mermaid
mindmap
  root((Server Roles))
    Web Server
    Database Server
    File Server
    Application Server
    Virtualization Host
    Domain Controller
```

> **Image placeholder:** `assets/server-hardware/day1-datacenter.jpg` — a photo of a real data center rack row.

---

## Topic 1.2 — Server Form Factors

The three main physical formats. Each trades off:

- Density
- Scalability
- Cost
- Cooling

```mermaid
flowchart TD
    F[Server Form Factors]

    F --> T[Tower]
    F --> R[Rack]
    F --> B[Blade]

    T --> T1[Looks like a desktop]
    T --> T2[Small office, low density]

    R --> R1[19-inch rack mounted]
    R --> R2[Measured in U - 1U = 1.75 in]

    B --> B1[Modular blades in a chassis]
    B --> B2[Shared power, cooling, network]
```

### Comparison

| Form Factor | Density | Scalability | Cost | Best For |
|------------|----------|-------------|------|----------|
| **Tower** | Low | Low | Low | Small office, single server |
| **Rack** | Medium-High | High | Medium | Enterprise data centers |
| **Blade** | Very High | Very High | High upfront | High-density compute |

### Understanding Rack Units (U)

A rack is **19 inches** wide and measured vertically in **U**, where:

**1U = 1.75 inches**

```mermaid
flowchart TB
    subgraph RACK[19-inch Rack]
        direction TB
        U42[42U ... top]
        S2[2U Server]
        S1[1U Server]
        U1[1U ... bottom]
    end
```

> **Image placeholder:** `assets/server-hardware/day1-formfactors.png` — side-by-side tower, rack, and blade photos.
