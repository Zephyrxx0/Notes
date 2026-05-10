# Unit 2 — Cloud Service Models: IaaS, PaaS, SaaS
**Course: TE7916 – Cloud Computing Tools and Techniques**

---

## 1. Overview of Cloud Service Models

Cloud computing delivers services through three primary models, stacked in layers:

```
┌────────────────────────────────────────────────────────────┐
│     Control / Governance  ───────────────────────────────► │
│                                                            │
│  ┌─────────────────────────────────────────────────────┐   │
│  │               SaaS (Software as a Service)          │   │
│  ├─────────────────────────────────────────────────────┤   │
│  │              PaaS (Platform as a Service)           │   │
│  ├─────────────────────────────────────────────────────┤   │
│  │           IaaS (Infrastructure as a Service)        │   │
│  ├────────────────┬───────────────┬────────────────────┤   │
│  │    Public      │    Hybrid     │     Private        │   │
│  └────────────────┴───────────────┴────────────────────┘   │
│     Economies of Scale ◄──────────────────────────────     │
│                              Flexibility of Purpose ───►   │
└────────────────────────────────────────────────────────────┘
```

---

## 2. Infrastructure as a Service (IaaS)

### Definition
Cloud services that deliver **infrastructure resources** — compute, storage, networking, and operating systems — as a service on demand.

### What Gets Virtualized
```
┌──────────────────────────────────────────────────────────┐
│  Virtual Machine 1       │  Virtual Machine 2            │
│  ┌──────────────────┐    │  ┌──────────────────┐         │
│  │   Application A1 │    │  │   Application A2 │         │
│  │   Operating Sys  │    │  │   Operating Sys  │         │
│  └──────────────────┘    │  └──────────────────┘         │
├──────────────────────────────────────────────────────────┤
│                     Hypervisor                           │  ← Software equivalent of h/w
├──────────────────────────────────────────────────────────┤
│   Processor  │  Memory  │  Network  │  Storage           │  ← Actual hardware
└──────────────────────────────────────────────────────────┘
```

### IaaS Responsibilities
| Managed by Provider | Managed by Customer |
|---|---|
| Virtualization layer | Applications |
| Servers | App data |
| Storage | Middleware |
| Networking | Operating System |

### Key IaaS Features
1. **Virtualization** — Multiple VMs on shared hardware (via Hypervisor).
2. **Resource Pooling** — CPU, memory, storage pooled and allocated on demand.
3. **Cloudbursting** — When private cloud hits capacity, overflow goes to public cloud.
4. **Multi-tenancy** — Multiple customers share same physical resources, logically isolated.
5. **Self-service provisioning** — Users create instances via portal without human intervention.
6. **Elastic scaling** — Resources scale up or down automatically.

### Cloudbursting in Detail
- A private cloud has finite capacity.
- When demand exceeds that capacity, workloads **"burst"** into a public cloud.
- IBM CloudBurst is a pre-packaged appliance ("Cloud in a Box") with BladeCenters, Ethernet switches, Management modules, Storage controllers, VMware Hypervisor, and High Availability SW.
- IBM CloudBurst configurations: Small (4 blades), Medium (5–14 blades), Large (15–28 blades).

### IaaS Examples
| Provider | Service | Description |
|---|---|---|
| Amazon | EC2 (Elastic Compute Cloud) | Self-service portal to create cloud server instances |
| Rackspace | Rackspace Cloud | Self-service portal to subscribe for cloud services |
| Microsoft | Azure Virtual Machines | IaaS compute service |
| IBM | IBM Cloud (SoftLayer) | Bare metal and virtual server infrastructure |

---

## 3. Platform as a Service (PaaS)

### Definition
PaaS provides a **platform allowing developers to build, run, and manage applications** without the complexity of maintaining the underlying infrastructure.

### PaaS Layer Stack
```
┌──────────────────────────────────────┐
│   Cloud Middleware                   │  ← OrangeScape, Wolf PaaS
│   (OraneScape, Wolf PaaS)            │
├──────────────────────────────────────┤
│   Cloud OS                           │  ← MS Windows Azure, Google App Engine
│   (MS Windows Azure, Google App Eng) │
├──────────────────────────────────────┤
│              PaaS                    │
└──────────────────────────────────────┘
```

### PaaS Responsibilities
| Managed by Provider | Managed by Customer |
|---|---|
| Hardware | Applications |
| Virtualization | App data |
| Servers | |
| Storage | |
| Networking | |
| OS | |
| Middleware | |

### Two Main PaaS Components
1. **The Computing Platform** — OS environment.
   - Example: Red Hat Enterprise, Microsoft Windows Azure, Google App Engine.
2. **The Middleware Stack** — Integration and processing software.
   - Example: OrangeScape, Wolf PaaS.

### Platform Services Infrastructure
A PaaS stack may include:
- **OS environments** — e.g., Red Hat Enterprise OS.
- **Web hosting with complete stack** — webserver, servlet container, database.
- **Secure computing environments** — all security protocols audited and compliance laws followed.
- **Software version control** — GIT, SVN, CVS.
- **Development environments** — compiler, debugger, test scripts.
- **Test environments** — pre-configured for test runs.

### Things to Consider Before Choosing PaaS
- Lock-in risk — moving from one PaaS to another may be difficult.
- Customization limitations — PaaS environments may restrict certain configurations.
- Security policies — ensure the platform meets compliance requirements.
- Scaling control — understand how and when autoscaling triggers.

### PaaS Examples
| Provider | Description |
|---|---|
| **Salesforce.com (Force.com)** | PaaS for building CRM-based business applications |
| **Google App Engine** | PaaS for deploying Python, Java, PHP apps on Google infrastructure |
| **Microsoft Azure (App Service)** | PaaS for web and mobile apps on Azure |
| **Amazon AWS (Elastic Beanstalk)** | PaaS wrapper around AWS infrastructure |
| **Rackspace** | Cloud platform services |
| **IBM Cloud Foundry** | Open-source PaaS platform hosted on IBM Cloud |

### Web Hosting PaaS Stack Example (IBM Cloud)
```
Instant Runtimes: Java, JS, PHP, Python, Go, Ruby
        ↑
Virtual Machines & IBM Containers & Docker
        ↑
Virtual Cloud Resources
        ↑
Bare Metal Cloud Resources (Storage + Compute + Network)
        ↑
SoftLayer (Automated Bare Metal Infrastructure)
```

---

## 4. Software as a Service (SaaS)

### Definition
SaaS is an implementation of a **business application or process that is developed on a cloud platform and hosted in a cloud infrastructure**. SaaS providers deliver domain-specific applications over the Internet, charging end users on a pay-per-usage basis.

### SaaS Responsibilities
| Managed by Provider | Managed by Customer |
|---|---|
| Application | Usage only |
| App data (infrastructure) | Personal data |
| Middleware | |
| OS | |
| Virtualization | |
| Servers, Storage, Networking | |

### SaaS Characteristics
- **Elasticity** — Scales automatically with user demand.
- **Multi-tenancy** — One application instance serves many customers.
- **Security** — Provider handles security and compliance.
- **Cost effectiveness** — No upfront licensing; subscription-based.
- **Self-service** — Users can sign up and start using immediately.

### SaaS Use Cases
| Category | Examples |
|---|---|
| Email | Gmail, Outlook 365 |
| CRM | Salesforce, HubSpot |
| Collaboration | Google Workspace, Microsoft Teams, Slack |
| ERP | SAP on Cloud, Oracle Cloud ERP |
| Business Intelligence | Tableau Online, Power BI |
| Content Management | SharePoint Online |

### SaaS Examples from Course Material
- **Google Docs, Gmail, Google Calendar** — End user productivity tools hosted on Google's cloud.
- **Google Workspace (G Suite)** — Full suite: Docs, Sheets, Slides, Drive, Gmail.

### SaaS Advantages
- No need to install or maintain software.
- Access from anywhere via a browser.
- Automatic updates handled by provider.
- Lower total cost of ownership.
- Rapid deployment — no setup time.

---

## 5. Business Process as a Service (BPaaS)

- Delivers **entire business process workflows** as a cloud-hosted service.
- Sits on top of SaaS in the cloud delivery model.
- Examples:
  - Employee Benefits Management.
  - Procurement.
  - Business Travel Management.
  - Industry-specific processes.

---

## 6. Comparison: IaaS vs PaaS vs SaaS

| Dimension | IaaS | PaaS | SaaS |
|---|---|---|---|
| Primary user | IT Architects / Network Engineers | Developers | End Users |
| Flexibility | Most flexible | Moderate | Least flexible |
| Control | Most control | Moderate | Least control |
| Operating cost | Higher (more to manage) | Medium | Lowest |
| Setup complexity | High | Medium | Low |
| Who manages OS | Customer | Provider | Provider |
| Who manages app | Customer | Customer | Provider |
| Scaling | Manual or custom | Automated (within PaaS) | Fully automated |
| Examples | AWS EC2, Rackspace | Google App Engine, Azure PaaS | Gmail, Salesforce |

---

## 7. Service Oriented Architecture (SOA) and Cloud

**SOA (Service Oriented Architecture)** is an architectural style where software components (services) communicate over a network through well-defined interfaces.

In the cloud context:
- Cloud applications are built as **collections of loosely coupled services**.
- Each service has a specific function and can be reused.
- Services communicate via APIs (typically REST or SOAP).
- SOA enables **multi-tier application architecture** in the cloud.

### Multi-tier Cloud Application Architecture
```
[Presentation Tier (Web Browser / Mobile App)]
           ↓ API calls
[Application Tier (Business Logic - Cloud VMs / Containers)]
           ↓ Database queries
[Data Tier (Cloud Databases / Storage Services)]
```

### Benefits of SOA in Cloud
- **Parallelization within cloud applications** — Services can run in parallel, increasing throughput.
- **Loose coupling** — Each service can be updated independently.
- **Reusability** — Common services shared across applications.
- **Scalability** — Individual services scale independently.

---

## 8. Elastic Computing and On-Demand Computing

### Elastic Computing
- The ability to **dynamically scale** computing resources (up or down) based on demand.
- Resources are provisioned when needed and released when not.
- Key to the "pay-as-you-use" model.

### On-Demand Computing
- Computing resources are available **immediately upon request**, without upfront reservation.
- No long-term commitments required.
- Enables rapid prototyping and development.

---

## Summary

The three core cloud service models — **IaaS, PaaS, and SaaS** — represent different levels of abstraction and responsibility. IaaS provides raw infrastructure for maximum control. PaaS provides a development platform for building applications. SaaS provides ready-to-use applications for end users. BPaaS sits above all three, delivering complete business processes. The models build on each other, with IaaS at the foundation. SOA principles guide the architecture of cloud applications, enabling elastic and on-demand computing through loosely coupled, scalable services.
