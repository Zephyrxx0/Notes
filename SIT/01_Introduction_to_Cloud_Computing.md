# Unit 1 — Introduction to Cloud Computing
**Course: TE7916 – Cloud Computing Tools and Techniques**

---

## 1. What is Cloud Computing?

Cloud computing is the delivery of computing resources — servers, storage, databases, networking, software, analytics, and more — **over the Internet ("the cloud")** on an **on-demand, pay-as-you-use** basis.

Instead of owning and maintaining physical hardware, organizations access technology services from a cloud provider and pay only for what they use.

> **Analogy:** Just like banking ATMs let you access your money without visiting the bank itself, cloud computing lets you access IT resources without owning them physically.

### Key Attributes of Cloud Computing
| Attribute | Description |
|---|---|
| Self-service | Users provision resources on demand without human intervention from the provider |
| Standardized services | Services are offered in a catalogue of standard components |
| Service catalog & ordering | Users browse and order services like an online shop |
| Flexible pricing | Pay for what you use; no large upfront costs |
| Metering & billing | Usage is tracked and billed granularly |
| Elastic scaling | Resources grow or shrink automatically with demand |
| Rapid provisioning | New systems can be deployed in minutes, not weeks |
| Advanced virtualization | Hardware is abstracted into virtual resources |

---

## 2. Origins of Cloud Computing

Cloud computing evolved from several earlier paradigms:

### 2.1 Grid Computing
- Combines computing resources from **multiple locations/administrative domains** to achieve a common goal.
- Distributes workload across many systems; each contributes individual resources.
- Example use cases: ATMs, back-end financial infrastructures, scientific research.
- Focuses on **sharing** computing resources.
- Types: Computational grid, Data grid, Collaborative grid.

### 2.2 Utility Computing
- Provides computing resources and infrastructure to customers **on demand**, charging them for specific usage (like a utility bill).
- Focuses on **acquiring** computing resources.
- Example: Amazon and Google establish utility services for computing, storage, and applications.
- Characteristics: Scalability, demand-based pricing, standardized services, automation.

### Grid vs. Utility Computing
| Parameter | Grid Computing | Utility Computing |
|---|---|---|
| Main focus | Sharing resources | Acquiring resources |
| Resource organization | Pooled from cooperating partners (Virtual Organizations) | Allocated/segregated per user requirements |
| Goal | Solve a common technical/scientific problem | Make infrastructure available per need, charge per use |
| Types | Computational, Data, Collaborative | Internal, External |
| Characteristics | Resource coordination, transparent access, dependable access | Scalability, demand pricing, automation |

---

## 3. Key Features of Cloud Computing (NIST Characteristics)

### 3.1 On-Demand Self-Service
Users can provision computing capabilities (server time, storage) **automatically**, without requiring human interaction from the service provider.

### 3.2 Broad Network Connectivity
Capabilities are available over the network and accessible via standard mechanisms (laptops, mobiles, tablets).

### 3.3 Location-Independent Resource Pooling
Provider resources are pooled to serve multiple customers using a **multi-tenant** model. Physical and virtual resources are dynamically assigned according to consumer demand. The user generally doesn't know the exact location of resources.

### 3.4 Rapid Flexibility (Elasticity)
Resources can be **elastically provisioned and released** — sometimes automatically — to scale rapidly outward and inward commensurate with demand.

### 3.5 Pay-as-You-Use (Measured Service)
Cloud systems automatically control and optimize resource usage. Usage is **metered and billed** at a granular level (per hour, per GB, etc.).

---

## 4. Traditional IT vs. Cloud Providers

| Parameter | Traditional IT | Cloud Computing |
|---|---|---|
| Provisioning | Manual, takes days/weeks | Automatic, minutes or hours |
| Utilization | Often 10–20% | Typically 60–90% |
| Monitoring | Manual intervention needed | Fully automated orchestration |
| Sizing | Manual resize for new needs | On-demand automatic rescaling |
| Staff | Many Full-Time Employees | ~1 administrator per 400 instances |
| Cost model | High upfront capital expenditure | Monthly running cost; near-zero initial hardware |
| Optimization | Manual rebalancing across hosts | Automated, no intervention needed |

---

## 5. Cloud Computing Business Value

Cloud computing delivers value in several dimensions:

### Business Value
- Provides creative ways for companies to address IT utilization.
- **Reduces capital expenses and operational costs.**
- Makes IT applications and infrastructure dynamically available.
- Provides rapid service delivery.
- Allows testing new plans with little delay (faster start-up for projects).

### Technological Value
| Capability | Value Delivered |
|---|---|
| Heritage of Grid Computing | Accelerate deployment of new applications |
| Resource capacity pooling | Serve core business computing needs |
| Virtualized resource pool | Gain flexibility to meet changing demands |
| Automation & self-service | Reduce manual management overhead |
| Scalability & agility | Respond to business changes quickly |
| Multi-tenancy | Share infrastructure costs across users |

> **Potential Inhibitors:** Strong network management needs, high bandwidth required, compliance with data regulations.

---

## 6. Business Impact of Cloud

### Substantial Savings
- Savings in power, operations, and hardware purchases.
- Avoids cost impact of over-provisioning and under-provisioning.

### New Opportunities
- Investment to support a new product is noticeably reduced.
- Shorter time between project approval and actual start of work.

### Cloud Addresses Traditional IT Issues
Cloud computing helps reduce or eliminate:
- Lost business opportunities (IT too slow to react).
- Long deployment timelines (weeks/months).
- Many people involved, creating high cost and complexity.
- Many manual steps prone to error.
- Huge upfront investment for new infrastructure.
- Server sprawl and low utilization.
- Compliance, auditing, and security patching costs.
- Unknown compute resource usage and costs.

---

## 7. Anatomy of a Cloud — Eight Major Components

A cloud is composed of eight major building blocks:

1. **Provisioning and Configuration Module** — Automates setup of resources.
2. **Monitoring and Optimization** — Tracks performance and adjusts resources.
3. **Metering and Chargeback** — Measures usage and allocates costs.
4. **IT Service Management** — Manages the service lifecycle.
5. **Orchestration** — Coordinates workflows across components.
6. **CMDB (Configuration Management Database)** — Stores infrastructure configuration data.
7. **Cloud Lifecycle Management Layer** — Manages the full life of cloud services.
8. **Service Catalog** — The menu of available services for users to order.

---

## 8. Cloud Computing Components (Workflow)

```
[Service Catalog]
       ↓
[Self-Service Portal] → [Service Request] → [Service Provisioning] → [Optimized Infrastructure]
       ↑_____________________________[Charge-Back]_________________________________|
```

| Stage | Benefit |
|---|---|
| Self-service portal | Improves customer satisfaction and responsiveness |
| Service request | Capacity management with validated change workflow |
| Service provisioning | Low/no-touch deployment, drive down operational costs |
| Optimized infrastructure | Improved server/power utilization |

---

## 9. What Makes Cloud Different?

### Without Cloud Computing
- Each workload has dedicated software, hardware, storage, networking.
- Service managed per-application silo.

### With Cloud Computing
- Virtualized resources pooled across workloads.
- Automated service management.
- Standardized services across all workloads.
- Location independent, rapid scalability, self-service.

---

## Summary

Cloud computing represents a fundamental shift from owning IT infrastructure to **consuming it as a service**. Its origins in grid and utility computing led to a model that is elastic, self-service, and pay-per-use. The core value propositions are **cost reduction, speed, flexibility, and scalability**. A cloud is composed of eight building blocks working together to deliver automated, on-demand IT services to businesses and end users.
