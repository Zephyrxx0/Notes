# Unit 1 & 2 — Cloud Architecture & Deployment Models
**Course: TE7916 – Cloud Computing Tools and Techniques**

---

## 1. Cloud Architecture — Layers Overview

Cloud architecture is organized into **layers**, each providing a different level of abstraction and service:

```
┌──────────────────────────────────────────┐
│          SaaS (Software as a Service)    │  ← End Users consume
├──────────────────────────────────────────┤
│        PaaS (Platform as a Service)      │  ← Developers build on
├──────────────────────────────────────────┤
│    IaaS (Infrastructure as a Service)    │  ← IT Architects use
├──────────────────────────────────────────┤
│         Physical Infrastructure          │  ← Servers, Storage, Network
└──────────────────────────────────────────┘
```

- As you move **up**, operating costs decrease and flexibility for the provider increases.
- As you move **down**, the customer has more control but more responsibility.

---

## 2. Cloud Deployment Models

Cloud can be deployed in four ways:

### 2.1 Public Cloud
- **Based on a standard cloud computing model.**
- Resources are available to the **general public**.
- Services may be free or offered on a **pay-per-usage** model.
- Provider owned and managed; access by subscription.
- **Benefits:** Low investment, good test/development environment for apps.
- **Risks:** Security concerns, IT organization may lose control over data-center functions.
- **Examples:** Amazon AWS, Google Cloud, Microsoft Azure, Salesforce.com.

### 2.2 Private Cloud
- A cloud computing infrastructure created by an organization **for its own internal use**.
- Client owned and managed; access defined by the client.
- **Benefits:** Fewer security concerns, IT organization retains control over data center.
- **Risks:** High investment hurdle in implementation, new operational processes required.
- **Tools:** VMware vCenter, VMware vSphere.

### 2.3 Hybrid Cloud
- A **composition of at least one private cloud and at least one public cloud.**
- Safe connections are needed between private and public clouds.
- Uses **Federation & Choice** to manage resources across clouds.
- **Benefits:** Operational flexibility, scalability.
- **Risks:** Still being developed, control of security between private and public clouds.

### 2.4 Community Cloud
- Shared infrastructure for a **specific community** with common concerns (e.g., universities, government agencies).

### Comparison: Private vs Public vs Hybrid
| Feature | Private Cloud | Public Cloud | Hybrid Cloud |
|---|---|---|---|
| Ownership | Client owned | Provider owned | Mixed |
| Access | Defined by client | Subscription | Both |
| Key advantage | Customization, security, privacy, availability, efficiency | Standardization, capital preservation, flexibility, time-to-deploy | Operational flexibility, scalability |
| Cost | High upfront | Low upfront | Medium |
| Security | High | Lower | Configurable |

---

## 3. Cloud Service Models (Delivery Models)

Cloud delivery models are broadly divided into **four major categories**:

### 3.1 Infrastructure as a Service (IaaS)
Cloud services that deliver **infrastructure resources** (compute, storage, networking, operating systems) as a service.

**What the cloud manages:** Virtualization, Servers, Storage, Networking.  
**What the user manages:** OS, Middleware, App Data, Application.

**Key Features:**
- **Virtualization** — Multiple VMs run on shared physical hardware via a hypervisor.
- **Resource pooling** — CPU pools and disk pools shared across tenants.
- **Cloudbursting** — Overflow capacity temporarily uses public cloud when private cloud is full.
- **Multi-tenancy** — Multiple customers share same physical infrastructure with isolated environments.

**Examples:**
- **Amazon EC2** (Elastic Compute Cloud) — self-service portal to create cloud server instances.
- **Rackspace** — provides self-service portal to subscribe for cloud services.

---

### 3.2 Platform as a Service (PaaS)
Provides a **platform allowing customers to develop, run, and manage applications** without dealing with the infrastructure.

**What the cloud manages:** Hardware, OS, Middleware.  
**What the user manages:** Application, App Data.

**PaaS Layer has two main components:**
1. **The Computing Platform** — The OS environment (e.g., Red Hat Enterprise, MS Windows Azure, Google App Engine).
2. **The Middleware Stack** — Cloud middleware (e.g., OrangeScape, Wolf PaaS).

**Platform Services Infrastructure includes:**
- OS environments (e.g., Red Hat Enterprise).
- Web hosting with complete stack (webserver, servlet container, database).
- Secure computing environments with compliance laws.
- Software version control (GIT, SVN, CVS).
- Development environments with compilers, debuggers, test scripts.
- Test environments pre-configured for test runs.

**Examples:**
- **Salesforce.com** — PaaS for CRM and business applications.
- **Amazon Web Services** — PaaS offerings alongside IaaS.
- **Rackspace** — PaaS services.
- **Google App Engine, Microsoft Azure** — Cloud OS platforms.

---

### 3.3 Software as a Service (SaaS)
An implementation of a business application or process that is **developed on a cloud platform and hosted in a cloud infrastructure**.

- SaaS providers deliver **domain-specific applications or services over the Internet**.
- End users are charged on a **pay-per-usage basis**.
- **Users consume** — they don't manage anything below the application.

**What the cloud manages:** Everything (Hardware, OS, Middleware, Application).  
**What the user manages:** Just their data/usage.

**SaaS is used for:**
- Email, CRM (Customer Relationship Management), Collaboration, ERP.
- Business intelligence services, content management services.

**Examples:**
- **Google Docs, Gmail, Google Calendar** — productivity tools.
- **Salesforce CRM** — customer relationship management.
- **Microsoft Office 365** — enterprise productivity.

---

### 3.4 Business Process as a Service (BPaaS)
- Delivers complete **business process workflows** as a cloud service.
- Examples: Employee Benefits Management, Procurement, Business Travel.
- Sits on top of SaaS in the service model stack.

---

## 4. IT Layers — Who Uses What

```
                    [Vendor]
                       |
          Provide ←  [IaaS]  ← Consume (Network Architects)
                       |
          Provide ←  [PaaS]  ← Consume (Developers)
                       |
          Provide ←  [SaaS]  ← Consume (End Users)
```

---

## 5. Cloud Delivery Infrastructure (Full Stack)

| Layer | Components |
|---|---|
| Infrastructure | Server (Processor, Memory, Nodes), Storage (Drives, Ephemeral, Persistent), Network (Internal, External, Inter-site), Facilities (Location, Power) |
| IaaS | Shared virtualized, dynamic provisioning |
| PaaS | Middleware, Database, Web 2.0 Application Runtime, Java Runtime, Development Tooling |
| SaaS | Collaboration, Financials, Industry Applications, CRM/ERP/HR |
| BPaaS | Employee Benefits Mgmt., Business Travel, Procurement, Industry-specific Processes |
| Governance | Security, resilience, performance, consumability |

---

## 6. Benefits of Cloud — Capability Improvements

| Capability | Legacy Environment | Cloud-Enabled Enterprise |
|---|---|---|
| Server/Storage Utilization | 10–20% | 70–90% |
| Self-service | None | Unlimited |
| Test Provisioning | Weeks | Minutes |
| Change Management | Months | Days/Hours |
| Release Management | Weeks | Minutes |
| Metering/Billing | Fixed cost model | Granular |
| Standardization | Complex | Self-Service |
| Payback period for new services | Years | Months |

---

## 7. Market Landscape

### Public Cloud Vendors
- Amazon (AWS)
- Google (Google Cloud)
- Microsoft (Azure)
- Salesforce.com

### Private Cloud Vendors
- IBM
- VMware
- Sun/Oracle

### Key Cloud Providers Today
Microsoft, Amazon (AWS), Google, IBM, Salesforce, Zoho.

---

## Summary

Cloud architecture is built around three core service models — **IaaS, PaaS, and SaaS** — stacked on physical infrastructure. These services are deployed using one of four deployment models: **public, private, hybrid, or community cloud**. Each model and service layer involves different tradeoffs between cost, control, flexibility, and security. The hybrid model is increasingly favored for combining the security of private cloud with the scalability of public cloud.
