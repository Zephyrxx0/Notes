# Unit 2 — Advanced Virtualization, Web 2.0, Browser as Platform & Cloud OS
**Course: TE7916 – Cloud Computing Tools and Techniques**

---

## 1. Types of Virtualization

Virtualization is not limited to servers. It can be applied across many IT domains:

### 1.1 Server Virtualization
- **Most common type** in cloud computing.
- One physical server runs multiple virtual servers (VMs).
- Managed by a **Hypervisor**.
- Examples: VMware vSphere, Microsoft Hyper-V, KVM, Xen.

### 1.2 Storage Virtualization
- Physical storage from multiple devices is pooled into a **single logical storage unit**.
- Storage can be managed centrally.
- Examples: SAN (Storage Area Network), NAS (Network Attached Storage), Amazon S3 (virtual storage).
- Benefits: Simplified management, better utilization, easy expansion.

### 1.3 Network Virtualization
- Multiple logical networks operate over the same **physical network infrastructure**.
- Examples: VLAN (Virtual LAN), VPN (Virtual Private Network), Software Defined Networking (SDN).
- Benefits: Isolation, security, flexible network topology.

### 1.4 Desktop Virtualization (VDI)
- The desktop environment (OS + applications) is hosted on a **remote server** and delivered to the user's device.
- Example: Citrix Virtual Apps, VMware Horizon.
- Benefits: Central management, thin clients, remote access.

### 1.5 Application Virtualization
- Applications run in an **isolated virtual environment**, separate from the underlying OS.
- Users can run apps without installing them on their machine.
- Examples: Java JVM, Microsoft App-V.

### 1.6 OS-Level Virtualization (Containerization)
- Multiple isolated user-space instances (containers) share the **same OS kernel**.
- Lighter than full VMs — no separate OS per container.
- Examples: **Docker**, LXC (Linux Containers), Kubernetes (orchestration).
- Benefits: Fast startup, low overhead, portable.

### Comparison: VMs vs Containers
| Feature | Virtual Machine | Container |
|---|---|---|
| Isolation | Full OS isolation | Process-level isolation |
| Boot time | Minutes | Seconds |
| Size | GBs | MBs |
| OS | Each VM has its own OS | Shares host OS kernel |
| Overhead | Higher | Lower |
| Use case | Full server virtualization | Microservices, app packaging |

### Summary Table of Virtualization Types
| Type | What is Virtualized | Examples |
|---|---|---|
| Server | Physical servers | VMware, Hyper-V, KVM, Xen |
| Storage | Storage devices | Amazon S3, SAN, NAS |
| Network | Network infrastructure | VLAN, VPN, SDN |
| Desktop (VDI) | Desktop environments | Citrix, VMware Horizon |
| Application | Individual applications | JVM, Microsoft App-V |
| OS/Container | OS processes | Docker, LXC, Kubernetes |

---

## 2. Grid Technology in Cloud Context

Grid technology is the predecessor and a key influence on cloud computing.

### What is Grid Technology?
- A **distributed computing model** that combines resources from multiple administrative domains.
- Allows heterogeneous computers to work together toward a common computational goal.
- Resources are shared across organizational boundaries (Virtual Organizations / VOs).

### Grid vs Cloud
| Aspect | Grid Computing | Cloud Computing |
|---|---|---|
| Resource sharing | Peer-to-peer style | Provider-to-consumer |
| Management | Decentralized | Centralized by provider |
| User interface | Complex, requires technical knowledge | Simple, self-service |
| Business model | Academic / collaborative | Commercial / pay-per-use |
| Focus | Solving large computational problems | Delivering IT services |
| Standardization | Less standardized | Highly standardized |

### Grid Technology → Cloud Evolution
```
Grid Computing (1990s–2000s)
     ↓ (Added business model + automation + service management)
Utility Computing
     ↓ (Added self-service + elasticity + broad network access)
Cloud Computing (2006–present)
```

---

## 3. Browser as a Platform

The **browser as a platform** concept means using the **web browser itself as the runtime environment** for applications, rather than the underlying OS.

### Why the Browser Became a Platform
- Modern browsers (Chrome, Firefox, Edge) are extremely capable.
- Support for rich standards: HTML5, CSS3, JavaScript, WebAssembly.
- No need to install software — applications run directly in the browser.
- Platform-independent — the same app runs on Windows, Mac, Linux, Android, iOS.

### Key Browser Technologies Enabling This
| Technology | Role |
|---|---|
| **HTML5** | Structure and semantic content |
| **CSS3** | Styling and layout |
| **JavaScript** | Client-side logic and interactivity |
| **AJAX** | Asynchronous data loading without page reload |
| **WebSockets** | Real-time two-way communication |
| **Web Storage (localStorage/sessionStorage)** | Client-side data persistence |
| **WebAssembly** | Near-native performance in browser |
| **Service Workers** | Offline capability, background sync |

### Browser as Platform Examples
- **Google Docs / Sheets / Slides** — Full office suite running in a browser.
- **Figma** — Professional design tool, entirely browser-based.
- **VS Code Web** — Code editor running in a browser (github.dev).
- **Gmail, Outlook Web** — Email clients in the browser.
- **Online IDEs** — Repl.it, CodePen, JSFiddle.

### Significance for Cloud
- Cloud applications are **primarily delivered through browsers**.
- This makes cloud services **device-agnostic** — any device with a browser can access the cloud.
- SaaS applications are the primary beneficiary of the browser-as-platform model.

---

## 4. Web 2.0

### What is Web 2.0?
**Web 2.0** refers to the second generation of web development and design, characterized by the shift from **static web pages (Web 1.0)** to **dynamic, user-generated content** and **interactive user interfaces**.

The term was popularized around 2004–2005.

### Web 1.0 vs Web 2.0
| Feature | Web 1.0 | Web 2.0 |
|---|---|---|
| Content | Created by website owners | User-generated |
| Interaction | Read-only (passive) | Read-write (participatory) |
| Technology | Static HTML | AJAX, JavaScript, CSS |
| Examples | Static company websites | YouTube, Wikipedia, Facebook |
| Role of user | Consumer | Contributor |
| Data | Locked in silos | Open APIs, mashups |

### Key Web 2.0 Technologies
1. **AJAX (Asynchronous JavaScript and XML)** — Allows parts of a page to update without full reload (e.g., Gmail inbox updates).
2. **RSS Feeds** — Syndicate content updates.
3. **Mashups** — Combining data/APIs from multiple sources (e.g., Google Maps API embedded in other services).
4. **Social networking** — Facebook, Twitter, LinkedIn.
5. **Wikis** — Collaborative content creation (Wikipedia).
6. **Blogs and microblogs** — WordPress, Twitter.

### Web 2.0 in the Cloud Context
- Web 2.0 applications are **cloud-native by nature** — they run in browsers, store data remotely, and scale dynamically.
- PaaS platforms often provide **Web 2.0 Application Runtime** environments.
- Web 2.0 enabled the **SaaS revolution** — delivering rich applications through the browser.
- AJAX-based applications blur the line between desktop and web apps.

---

## 5. Automatic Systems / Automation in Cloud

**Automation** is one of the defining characteristics that separates cloud computing from traditional virtualization.

### What is Automated in Cloud?
| Process | Manual (Pre-Cloud) | Automated (Cloud) |
|---|---|---|
| Provisioning | IT admin manually sets up servers | APIs provision VMs in minutes |
| Scaling | Admin adds/removes servers manually | Auto-scaling rules trigger automatically |
| Monitoring | Humans check dashboards | Automated alerts and remediation |
| Patching | Manual scheduling and execution | Automated patch management |
| Backup | Manual or scripted | Policy-driven automated backups |
| Load balancing | Manual server weighting | Dynamic, automated load balancers |
| Billing | Manual invoices | Usage-based automated metering and billing |

### Key Automation Technologies
- **Infrastructure as Code (IaC)** — Define infrastructure in code (e.g., Terraform, AWS CloudFormation).
- **Configuration Management** — Automate server configuration (e.g., Ansible, Puppet, Chef).
- **CI/CD Pipelines** — Automate build, test, and deploy workflows.
- **Orchestration** — Coordinate multiple automated workflows (e.g., Kubernetes, Apache Airflow).
- **Auto-scaling policies** — Automatically scale up/down based on CPU/memory thresholds.

### Why Automation Matters
- Enables **rapid provisioning** (minutes, not days).
- Reduces human error.
- Allows one administrator to manage hundreds or thousands of cloud instances.
- Makes **elastic computing** possible at scale.

---

## 6. Cloud Computing Operating System (Cloud OS)

### What is a Cloud OS?
A **Cloud Operating System** (or Cloud OS) is software that manages and orchestrates computing resources **across an entire cloud infrastructure**, rather than just a single machine.

It is analogous to how a traditional OS manages resources on one computer — a Cloud OS manages resources across **entire data centers or distributed cloud infrastructure**.

### Traditional OS vs Cloud OS
| Feature | Traditional OS | Cloud OS |
|---|---|---|
| Scope | Single machine | Entire data center / cloud |
| Resources managed | CPU, RAM, Storage of one computer | Thousands of servers, storage arrays, networks |
| Examples | Windows, Linux | Google Borg, OpenStack, Microsoft Azure Fabric |
| User interaction | Desktop GUI / Terminal | API calls, Web console |

### Examples of Cloud OS / Platforms
| Cloud OS / Platform | Description |
|---|---|
| **OpenStack** | Open-source cloud operating system managing compute, storage, networking |
| **Google Borg** | Google's internal cluster management system (precursor to Kubernetes) |
| **Microsoft Azure Service Fabric** | Manages distributed microservices across clusters |
| **VMware vCloud** | Cloud management platform on top of VMware virtualization |
| **Amazon AWS** | Proprietary cloud OS managing AWS infrastructure globally |
| **IBM Cloud** | IBM's cloud management platform |

### Cloud OS Responsibilities
1. **Resource abstraction** — Hide complexity of physical infrastructure.
2. **Resource allocation** — Assign resources to workloads dynamically.
3. **Scheduling** — Decide where to run each workload.
4. **Fault tolerance** — Detect and recover from failures automatically.
5. **Networking** — Manage virtual networks and connectivity.
6. **Security** — Enforce access controls and isolation.
7. **Metering** — Track resource usage for billing.

### OpenStack — Key Components
OpenStack is a widely used open-source Cloud OS:
- **Nova** — Compute (manages VMs).
- **Swift** — Object storage.
- **Cinder** — Block storage.
- **Neutron** — Networking.
- **Horizon** — Dashboard (web UI).
- **Keystone** — Identity and authentication.
- **Glance** — Image service (VM templates).

---

## Summary

Advanced virtualization encompasses multiple types — server, storage, network, desktop, application, and OS-level (containers). Grid technology laid the foundation for cloud computing by pioneering distributed resource sharing. The browser-as-a-platform concept, powered by Web 2.0 technologies like AJAX and HTML5, enables SaaS delivery to any device. Automation is what distinguishes cloud from ordinary virtualization — enabling elastic, self-service, and metered computing at scale. Finally, the Cloud OS manages entire data centers as one unified resource pool, analogous to how a traditional OS manages a single computer.
