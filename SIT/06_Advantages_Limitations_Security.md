# Unit 1 — Advantages, Limitations & Security of Cloud Computing
**Course: TE7916 – Cloud Computing Tools and Techniques**

---

## 1. Advantages of Cloud Computing

Cloud computing delivers benefits to multiple stakeholders:

### 1.1 For IT Customers
- **Ability to elastically scale resources** while maintaining high quality of service.
- No need to forecast and purchase capacity in advance.
- Resources available exactly when needed.

### 1.2 For IT Analysts
- **Elastically scale resources at significantly lower incremental management cost.**
- Advanced orchestration capabilities reduce administration overhead.

### 1.3 For End Users
- **Anywhere access to applications through a simplified user interface.**
- Access from any device — laptop, tablet, smartphone.
- No need for software installation or updates.

### 1.4 For Financial Analysts
- **Rapid time to market for new services.**
- Anywhere access to applications through a simplified user interface.
- Investment to support new products is noticeably reduced.

### Common Attributes (Advantages) of Cloud
- **Enhanced user experience** — Simpler, more consistent interfaces.
- **Elastic scaling** — Resources expand or contract based on demand.
- **Automated provisioning** — No manual setup needed.
- **Highly virtualized** — Maximum use of hardware.
- **Flexible pricing** — Pay only for what you use.

---

## 2. Benefits in Detail

### 2.1 Scalability
- Systems can **scale horizontally** (add more instances) or **vertically** (increase resources in existing instances).
- No need to predict peak demand years in advance.
- Example: A retail website that scales up on Black Friday and scales down afterward.

### 2.2 Cost Reduction
- **Capital Expenses (CapEx)** are converted to **Operational Expenses (OpEx)**.
- No large upfront investment in hardware.
- Pay-per-use billing aligns costs to actual usage.
- Shared infrastructure across many users = economy of scale.

### 2.3 Flexibility and Agility
- New applications can be deployed in minutes.
- Development teams can spin up test environments instantly.
- Supports rapid iteration and prototyping.

### 2.4 Reliability and High Availability
- Cloud providers run **multiple data centers** in different regions.
- Data can be replicated across locations.
- Automatic failover if one region goes down.

### 2.5 Security (Provider-Managed)
- Major providers invest heavily in physical and cybersecurity.
- Automated patching and updates.
- Compliance certifications (ISO 27001, SOC 2, PCI-DSS, HIPAA).

---

## 3. Limitations and Challenges of Cloud Computing

While cloud has many advantages, it is important to understand its limitations — especially for sensitive workloads.

### 3.1 Sensitive Data
- **Data stored in the cloud is physically located on the provider's servers.**
- Concerns about data privacy, unauthorized access, or data leakage.
- Regulated industries (healthcare, banking, government) may face restrictions on where data can be stored.
- Example risk: Patient health records (PHI) stored with a third-party cloud provider.

### 3.2 Application Development Challenges
- Applications must be **re-architected** to take advantage of cloud elasticity.
- Legacy monolithic applications may not run efficiently on cloud infrastructure.
- Developers must learn new tools, APIs, and architectural patterns (microservices, serverless).

### 3.3 Third-Party Security Level
- You are trusting the cloud provider to secure your data.
- **Shared Responsibility Model:**
  - Provider secures the cloud infrastructure.
  - Customer is responsible for securing their applications, data, and access management.
- A breach at the provider level can affect thousands of customers simultaneously.

### 3.4 Issues of Regularity / Government Policies
- **Data sovereignty** — Governments may require data to be stored within national borders.
- Example: European GDPR requires personal data of EU citizens to stay within the EU.
- Financial regulators (RBI, SEC, FCA) may restrict cloud usage for certain financial data.
- Cloud providers must comply with local laws, which can vary dramatically between countries.

### 3.5 Vendor Lock-in
- Migrating from one cloud provider to another is complex and costly.
- Proprietary services (AWS Lambda, Azure Cosmos DB) are difficult to replicate elsewhere.
- Organizations may become dependent on one provider's pricing and terms.
- **Mitigation:** Use open standards, containers, and multi-cloud strategies.

### 3.6 Internet Dependency
- Cloud services require a **reliable internet connection**.
- Connectivity outages = inability to access applications or data.
- Latency can be an issue for real-time applications.

### 3.7 Limited Customization
- SaaS and PaaS may not offer the level of customization some organizations need.
- You are constrained by what the provider offers.

### 3.8 Downtime and Service Outages
- Cloud providers are not immune to outages.
- A major provider outage can affect thousands of businesses simultaneously.
- Example: AWS us-east-1 outages in 2011 and 2021.

---

## 4. Cloud Security

Security in cloud computing has several dimensions:

### 4.1 The Shared Responsibility Model
```
PROVIDER RESPONSIBILITY:                    CUSTOMER RESPONSIBILITY:
- Physical data center security             - Access management (IAM)
- Network infrastructure                    - Data encryption
- Hypervisor / virtualization layer         - Application security
- Service availability (SLA)               - User authentication
- Compliance of the infrastructure          - Data backup strategy
```

### 4.2 Key Security Concerns in Cloud

#### Data Security
- Data in transit should be encrypted (TLS/SSL).
- Data at rest should be encrypted (AES-256).
- Access to data should be controlled via IAM policies.

#### Identity and Access Management (IAM)
- Principle of least privilege — give only the access needed.
- Multi-factor authentication (MFA) should be enforced.
- Role-based access control (RBAC).

#### Network Security
- Virtual Private Clouds (VPCs) isolate network traffic.
- Security groups and firewalls control inbound/outbound traffic.
- VPNs for secure connections between on-premises and cloud.

#### Compliance and Audit
- Logs must be maintained (CloudTrail on AWS, Activity Logs on Azure).
- Regular audits and penetration testing.
- Certifications: ISO 27001, SOC 2 Type II, PCI-DSS, HIPAA, GDPR.

### 4.3 Amazon Web Services (AWS) Security — Overview
Amazon EC2 (Elastic Compute Cloud) offers:
- **Security Groups** — Virtual firewalls controlling instance-level traffic.
- **Key Pairs** — SSH authentication for Linux instances, RDP for Windows.
- **VPC (Virtual Private Cloud)** — Isolated network environment.
- **IAM Roles** — Assign permissions to EC2 instances.
- **EBS Encryption** — Encrypt storage volumes.

---

## 5. Pros and Cons Summary

### Pros of Cloud
| Advantage | Description |
|---|---|
| **Scalability** | Scale resources up or down on demand |
| **Cost** | Convert CapEx to OpEx; pay only for use |
| **Flexibility** | Access from anywhere, any device |
| **Agility** | Deploy new services quickly |
| **Elasticity** | Automatic resource adjustment |

### Cons of Cloud
| Limitation | Description |
|---|---|
| **Security** | Data breaches, unauthorized access, shared infrastructure risks |
| **Lack of control** | Limited customization and control over infrastructure |
| **Standardization** | Provider's standards may not match all needs |
| **Connectivity** | Requires reliable internet |
| **Vendor lock-in** | Difficult to migrate between providers |

---

## 6. High Performance Computing in Cloud

Cloud is increasingly used for HPC (High Performance Computing) workloads:

- Clusters of VMs can be provisioned on demand for compute-intensive tasks.
- **Utility computing model** — Pay for CPU time used, not for idle cluster.
- Used in: Scientific simulation, genomics, financial modelling, machine learning.
- Traditional HPC clusters required months of procurement; cloud provides them in minutes.
- Example: AWS HPC clusters, Google Cloud TPUs, Azure HPC.

### Enterprise Grid Computing in Cloud
- Enterprise grids (traditionally on-premises) can be extended to the cloud.
- Burst from on-premises grid to cloud during peak demand.
- Combine private grid + public cloud = **hybrid compute grid**.

---

## Summary

Cloud computing offers significant advantages in scalability, cost, flexibility, and agility. However, it also presents challenges around data security, compliance, vendor lock-in, and connectivity. Understanding the **Shared Responsibility Model** is critical — the cloud provider secures the infrastructure, while the customer is responsible for securing their data and applications. For sensitive or regulated workloads, a **private or hybrid cloud** may be the appropriate choice. Despite limitations, cloud computing has proven transformative for both businesses and the delivery of high-performance computing resources.
