# Quick Reference — Key Terms & Exam Prep
**Course: TE7916 – Cloud Computing Tools and Techniques | Units 1 & 2**

---

## 1. Essential Definitions

| Term | Definition |
|---|---|
| **Cloud Computing** | Delivery of computing resources over the Internet on an on-demand, pay-as-you-use basis |
| **Virtualization** | Creating a software-based version of hardware/software resources |
| **Hypervisor (VMM)** | Software layer that creates and manages virtual machines |
| **Virtual Machine (VM)** | A software emulation of a physical computer |
| **IaaS** | Infrastructure as a Service — provides virtualized compute, storage, network |
| **PaaS** | Platform as a Service — provides a development/runtime platform |
| **SaaS** | Software as a Service — provides complete applications over the Internet |
| **BPaaS** | Business Process as a Service — delivers complete business workflows as cloud services |
| **Public Cloud** | Infrastructure owned by provider, available to general public |
| **Private Cloud** | Infrastructure owned/operated by a single organization for internal use |
| **Hybrid Cloud** | Combination of private and public cloud environments |
| **Community Cloud** | Shared infrastructure for a specific community with common interests |
| **Elasticity** | Ability to scale resources up or down automatically based on demand |
| **Scalability** | Ability of a system to handle growing workloads |
| **Multi-tenancy** | Multiple customers sharing the same physical infrastructure, logically isolated |
| **Resource Pooling** | Provider resources pooled and dynamically assigned to multiple customers |
| **Cloudbursting** | Overflow of on-premises/private cloud capacity into a public cloud |
| **SOA** | Service Oriented Architecture — software components communicate via well-defined interfaces |
| **Grid Computing** | Combines resources from multiple locations to achieve a common goal |
| **Utility Computing** | Provides computing resources on demand, charged per use |
| **Web 2.0** | Second generation of web focusing on user participation and dynamic content |
| **AJAX** | Asynchronous JavaScript and XML — allows web pages to update without full reload |
| **Cloud OS** | Software managing resources across an entire cloud infrastructure |
| **Dom0** | Privileged management VM in Xen architecture |
| **DomU** | Unprivileged guest VM in Xen architecture |
| **Full Virtualization** | Guest OS runs unmodified; hypervisor translates privileged instructions |
| **Para-Virtualization** | Guest OS is modified to use hypercalls; more efficient than full virtualization |
| **Hypercall** | Direct call from a para-virtualized OS to the hypervisor |
| **Shared Responsibility Model** | Provider secures infrastructure; customer secures data and apps |
| **CapEx** | Capital Expenditure — large upfront purchases (e.g., buying servers) |
| **OpEx** | Operational Expenditure — ongoing costs (e.g., cloud subscription) |

---

## 2. Key Comparisons

### Cloud vs Virtualization
```
Virtualization = Technology (creates virtual resources)
Cloud = Service + Business Model + Automation + Virtualization
```

### IaaS vs PaaS vs SaaS — Who Manages What
```
Layer:          IaaS Customer  |  PaaS Customer  |  SaaS Customer
Application:    ✓ Customer     |  ✓ Customer      |  ✗ Provider
App Data:       ✓ Customer     |  ✓ Customer      |  ✗ Provider
Middleware:     ✓ Customer     |  ✗ Provider      |  ✗ Provider
OS:             ✓ Customer     |  ✗ Provider      |  ✗ Provider
Virtualization: ✗ Provider     |  ✗ Provider      |  ✗ Provider
Servers:        ✗ Provider     |  ✗ Provider      |  ✗ Provider
Storage:        ✗ Provider     |  ✗ Provider      |  ✗ Provider
Networking:     ✗ Provider     |  ✗ Provider      |  ✗ Provider
```

### Full Virtualization vs Para-Virtualization
| Aspect | Full Virtualization | Para-Virtualization |
|---|---|---|
| OS modification | Not required | Required (recompiled) |
| Mechanism | Binary translation | Hypercalls |
| Performance | Slightly lower | Better |
| Example | VMware | Xen (older) |

---

## 3. The Eight Key Features (NIST Cloud Characteristics)

1. On-demand self-service
2. Broad network access
3. Resource pooling (location-independent)
4. Rapid elasticity (flexibility)
5. Measured service (pay-as-you-use)
6. Multi-tenancy
7. Virtualization (advanced)
8. Automation

---

## 4. The Eight Components of a Cloud (Anatomy)

1. Provisioning and Configuration Module
2. Monitoring and Optimization
3. Metering and Chargeback
4. IT Service Management
5. Orchestration
6. CMDB (Configuration Management Database)
7. Cloud Lifecycle Management Layer
8. Service Catalog

---

## 5. Important Examples to Remember

| Service | Type | Provider |
|---|---|---|
| EC2 (Elastic Compute Cloud) | IaaS | Amazon AWS |
| Rackspace Cloud Servers | IaaS | Rackspace |
| Google App Engine | PaaS | Google |
| Microsoft Azure App Service | PaaS | Microsoft |
| Salesforce Force.com | PaaS | Salesforce |
| IBM Cloud Foundry | PaaS | IBM |
| Gmail, Google Docs | SaaS | Google |
| Salesforce CRM | SaaS | Salesforce |
| Microsoft Office 365 | SaaS | Microsoft |
| IBM CloudBurst | IaaS appliance | IBM |

---

## 6. Pros and Cons of Each Cloud Architecture

| | Private Cloud | Public Cloud | Hybrid Cloud |
|---|---|---|---|
| **Pros** | Security, control, customization | Low cost, scalability, no upfront investment | Flexibility, scalability, cost optimization |
| **Cons** | High upfront cost, complex setup | Security concerns, loss of control | Complex to manage, security between clouds |

---

## 7. Grid vs Utility vs Cloud

| Aspect | Grid | Utility | Cloud |
|---|---|---|---|
| Focus | Sharing resources | Acquiring resources | Delivering IT services |
| Organization | Peer-to-peer, VOs | Provider-consumer | Provider-consumer |
| Model | Academic/collaborative | Commercial | Commercial |
| Self-service | No | Limited | Yes |
| Elasticity | Limited | Limited | Full |

---

## 8. Common Exam-Style Questions and Answers

**Q: What are the five key characteristics of cloud computing?**  
A: On-demand self-service, broad network access, resource pooling, rapid elasticity, and measured service.

**Q: What is the difference between full virtualization and para-virtualization?**  
A: In full virtualization, the guest OS runs unmodified and the hypervisor translates privileged instructions via binary translation. In para-virtualization, the guest OS is modified to issue hypercalls directly to the hypervisor, which is more efficient.

**Q: What is cloudbursting?**  
A: When a private cloud reaches its capacity, workloads overflow (burst) into a public cloud environment automatically, ensuring continuous service availability.

**Q: What is the Shared Responsibility Model in cloud security?**  
A: The cloud provider is responsible for securing the underlying infrastructure (hardware, virtualization, network). The customer is responsible for securing their data, applications, and access management.

**Q: What is multi-tenancy?**  
A: Multiple customers (tenants) sharing the same physical cloud infrastructure while being logically isolated from each other. This is common in SaaS (shared application) and IaaS (shared hardware).

**Q: How does cloud differ from virtualization?**  
A: Virtualization is a technology that creates virtual resources. Cloud computing is a service model that uses virtualization as one of its building blocks, combined with service management, a business model, automation, and self-service capabilities.

**Q: What are the deployment models in cloud?**  
A: Public cloud (provider-owned, available to all), Private cloud (organization-owned, internal use), Hybrid cloud (combination of private + public), Community cloud (shared among a specific community).

**Q: What is SOA and why is it relevant to cloud?**  
A: Service Oriented Architecture structures software as loosely coupled, reusable services that communicate via APIs. In cloud, applications are built as collections of cloud services that can be scaled independently, making SOA principles essential for cloud application design.

**Q: What is Web 2.0 and how does it relate to cloud?**  
A: Web 2.0 refers to the era of user-generated content, interactive web applications, and AJAX-based technologies. It's closely related to cloud as SaaS applications are typically Web 2.0 applications — dynamic, browser-based, and highly interactive.

**Q: What are the eight components (anatomy) of a cloud?**  
A: Provisioning & Configuration Module, Monitoring & Optimization, Metering & Chargeback, IT Service Management, Orchestration, CMDB, Cloud Lifecycle Management Layer, Service Catalog.

---

## 9. Quick Study Notes

### Remember the "aaS" hierarchy:
```
Hardware → IaaS → PaaS → SaaS → BPaaS
(More control)        →        (More simplicity)
(Less managed)        →        (Fully managed)
```

### Remember Cloud vs Virtualization:
```
Virtualization provides INFRASTRUCTURE FLEXIBILITY.
Cloud provides SERVICES + BUSINESS MODEL on top.
```

### Remember deployment models by control:
```
Most control ← Private → Hybrid → Community → Public → Least control
```
