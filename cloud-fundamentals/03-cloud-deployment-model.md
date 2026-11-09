# Cloud Deployment Models

## 1. What is a Cloud Deployment Model?

A cloud deployment model describes how cloud infrastructure is owned, deployed, accessed and managed.

Four common models:
- **Public Cloud**
- **Private Cloud**
- **Hybrid Cloud**
- **Multi-Cloud**

### Service Model vs Deployment Model
- **Service model:** What service are we consuming? (IaaS, PaaS, SaaS, FaaS)
- **Deployment model:** How and where is the cloud environment deployed? (Public, Private, Hybrid, Multi-Cloud)

## 2. Public Cloud

A public cloud is an environment where a third-party provider owns and operates infrastructure and offers services to multiple customers over a network.

**Examples:** Oracle Cloud Infrastructure (OCI), Amazon Web Services (AWS), Microsoft Azure and Google Cloud Platform (GCP).

### How it works
1. An organization creates an account or tenancy.
2. It provisions compute, networking, databases and storage.
3. It deploys applications.
4. It pays according to resource consumption and service pricing.

Multiple customers use the provider's infrastructure with logical isolation and security controls.

**Advantages**
- No need to purchase physical servers.
- Fast provisioning and flexible scaling.
- Access to provider-operated global infrastructure.
- Pay-as-you-go options.
- Provider manages physical data centers and hardware.

**Considerations**
- Less control over underlying physical infrastructure.
- Costs can grow without monitoring and governance.
- Customers remain responsible for workload and security configurations.
- Regulatory and data-residency requirements must be considered.

**Example:** A startup hosts an e-commerce application using OCI Compute, Object Storage, a database and a Load Balancer.

**DevOps connection:** Provision infrastructure using Terraform, push images to OCIR and deploy applications on OKE.

## 3. Private Cloud

A private cloud is a cloud environment dedicated to a single organization. It may be hosted in the organization's own data center or by a third-party provider.

Private cloud does not necessarily mean the organization owns every physical server. The key characteristic is that the environment is dedicated to that organization.

**Examples**
- An organization operating its own VMware-based private cloud.
- A private cloud built using OpenStack.
- Dedicated private cloud infrastructure hosted by a third party.

**How it works**
1. The organization establishes dedicated infrastructure.
2. It uses virtualization and cloud management software.
3. It creates virtual machines, networks and storage.
4. Internal teams provision resources through a self-service platform.
5. The organization or hosting provider manages the environment.

**Advantages**
- Greater control over infrastructure and configuration.
- Dedicated environment for one organization.
- Can support specific regulatory and data-residency requirements.
- Custom security and network architecture.

**Considerations**
- Infrastructure and operational costs can be higher.
- Skilled administrators are required.
- Scaling may require capacity planning and hardware.
- More responsibility for maintenance and lifecycle management.

**Example:** A bank operates sensitive workloads in a private cloud to retain dedicated infrastructure and greater control.

**Important:** Private cloud is not automatically more secure than public cloud. Security depends on architecture, configuration, operations and governance.

## 4. Hybrid Cloud

Hybrid cloud combines private infrastructure (such as an on-premises data center or private cloud) with public cloud services. Workloads and data can operate across both environments.

### Example architecture
1. Keep the existing production database in the on-premises data center.
2. Deploy the application frontend or microservices on OCI.
3. Connect both environments over a secure network.
4. Continue running selected services on-premises.
5. Deploy new workloads directly to OCI.

### OCI connectivity options

- **Site-to-Site VPN:** Establishes an encrypted connection between an on-premises network and an OCI VCN over the internet.
- **FastConnect:** Provides a dedicated private connectivity option between an organization's network and OCI.
- **Dynamic Routing Gateway (DRG):** A virtual routing component that connects a VCN to external networks, including on-premises networks through supported connectivity options.

VPN and FastConnect are connectivity options. DRG provides routing connectivity between the OCI VCN and supported external networks.

**Advantages**
- Gradual cloud migration.
- Existing infrastructure investments can continue to be used.
- Sensitive workloads can remain on-premises when required.
- Public cloud resources can provide additional capacity.
- Flexible workload placement.

**Considerations**
- More complex network architecture.
- Troubleshooting across environments can be difficult.
- Identity and security policies must be coordinated.
- Data synchronization and latency need planning.

**Example:** An on-premises Oracle database communicates with application microservices running on OKE. OCI Object Storage is used for backups.

**DevOps connection:** Troubleshooting pod-to-database connectivity requires knowledge of VPN, routing, DNS, firewall rules, security policies and latency.

## 5. Multi-Cloud

Multi-cloud means an organization uses services from two or more public cloud providers.

**Example**
- OCI for enterprise database workloads.
- AWS for an analytics platform.
- Azure for Microsoft ecosystem integrations.

**How it works**
1. Database workloads run on OCI.
2. Analytics workloads run on AWS.
3. Applications exchange data across cloud environments when required.
4. Monitoring and security policies are coordinated.
5. The organization manages costs and operations across providers.

**Advantages**
- Access to services from multiple providers.
- Flexibility in workload placement.
- Reduced dependence on one provider for certain workloads.
- Ability to use provider-specific capabilities.

**Considerations**
- More complex operations and monitoring.
- Different IAM models and security configurations.
- Multiple billing and cost-management systems.
- Cross-cloud networking can be complicated.
- Teams need broader cloud expertise.

**Example:** A company uses OCI for its production database and AWS for a separate analytics platform.

**Important:** Using OCI for production and AWS for development is multi-cloud if both providers are actively used. It does not mean the same application must run on both providers.

## 6. Hybrid Cloud vs Multi-Cloud

| Feature | Hybrid Cloud | Multi-Cloud |
|---|---|---|
| Environment | Private/on-premises + public cloud | Two or more cloud providers |
| Example | On-premises + OCI | OCI + AWS |
| Main reason | Combine existing infrastructure with cloud | Use multiple cloud providers |
| Main complexity | Connectivity and integration | Cross-cloud operations and integration |

Remember:
- On-premises + OCI = Hybrid Cloud.
- OCI + AWS = Multi-Cloud.
- On-premises + OCI + AWS = Both Hybrid and Multi-Cloud.

These models can coexist; they are not always mutually exclusive.

## 7. Comparison of Deployment Models

| Feature | Public Cloud | Private Cloud | Hybrid Cloud | Multi-Cloud |
|---|---|---|---|---|
| Infrastructure | Provider-owned/shared | Dedicated to one organization | Private + public | Multiple providers |
| Ownership | Cloud provider | Organization or hosting provider | Mixed | Multiple providers |
| Scalability | Generally high | Depends on capacity | Across environments | Depends on providers |
| Control | Less physical control | Greater infrastructure control | Mixed | Depends on provider |
| Complexity | Moderate | Moderate to high | High | High |
| Example | OCI | OpenStack private cloud | On-premises + OCI | OCI + AWS |

Actual cost, control, scalability and complexity depend on architecture and services selected.

## 8. DevOps and Kubernetes Example

Consider an enterprise architecture:

| Component | Location |
|---|---|
| Legacy database | On-premises |
| Main microservices | OCI OKE |
| Container registry | OCI OCIR |
| Backup storage | OCI Object Storage |
| Analytics platform | AWS |
| Connectivity | VPN / FastConnect / cross-cloud networking |

A DevOps engineer may be responsible for:
1. Provisioning infrastructure through Terraform.
2. Deploying applications to OKE.
3. Configuring secure connectivity.
4. Managing CI/CD pipelines.
5. Monitoring workloads across environments.
6. Troubleshooting application and network connectivity.
7. Managing access, security and cloud costs.

## 9. Interview Questions and Answers

### Q1. What is a public cloud?
A public cloud is an environment where a third-party provider owns and operates infrastructure and offers services to multiple customers over a network.

### Q2. What is a private cloud?
A private cloud is a cloud environment dedicated to one organization. It may be hosted on-premises or by a third-party provider.

### Q3. What is hybrid cloud?
Hybrid cloud combines private infrastructure, such as an on-premises data center, with public cloud services, allowing workloads and data to operate across both.

### Q4. What is multi-cloud?
Multi-cloud means using cloud services from two or more cloud providers, such as OCI and AWS.

### Q5. What is the difference between hybrid cloud and multi-cloud?
Hybrid cloud combines private infrastructure with public cloud, whereas multi-cloud uses services from multiple cloud providers. An organization can use both approaches together.

### Q6. Why do organizations choose hybrid cloud?
Organizations may choose hybrid cloud to migrate gradually, retain existing infrastructure, meet regulatory requirements and use public cloud resources for scalability.

### Q7. Can an organization use both hybrid cloud and multi-cloud?
Yes. For example, an organization can maintain an on-premises database, deploy applications on OCI and use AWS for analytics.

### Q8. Is public cloud always cheaper than private cloud?
No. Public cloud can reduce upfront infrastructure investment, but actual costs depend on resource consumption, architecture, pricing and governance.

### Q9. What is the role of DRG in hybrid cloud connectivity?
A Dynamic Routing Gateway (DRG) is an OCI virtual routing component that connects a VCN to external networks, including on-premises networks through supported connectivity options such as Site-to-Site VPN or FastConnect.

### Q10. What is the difference between Site-to-Site VPN and FastConnect?
Site-to-Site VPN provides encrypted connectivity over the internet. FastConnect provides a dedicated private connectivity option to OCI. The choice depends on performance, availability, cost and network design.

## 10. Practical Exercise

Identify the deployment model and explain why.

1. A startup hosts its complete application on OCI Compute and OCI Object Storage.
2. A bank operates its own dedicated cloud infrastructure in its data center.
3. A company keeps its database on-premises but runs its application on OCI OKE.
4. A company uses OCI for databases and AWS for analytics.

### Suggested answers
1. **Public Cloud** – consumes services from a public cloud provider.
2. **Private Cloud** – the environment is dedicated to one organization.
3. **Hybrid Cloud** – combines on-premises infrastructure with public cloud services.
4. **Multi-Cloud** – actively uses two public cloud providers.

## 11. Interview Scenario: On-Premises Database with OKE

**Question:** Your organization has an on-premises data center. Management wants to migrate applications to OCI, but the production database must remain on-premises due to regulatory requirements. The application should run on OKE and communicate securely with the database.

**Recommended model:** Hybrid Cloud.

**Suggested architecture**
1. Deploy application microservices on OCI OKE.
2. Keep the production database on-premises.
3. Establish connectivity using Site-to-Site VPN or FastConnect.
4. Use a DRG to connect the OCI VCN to the on-premises network through the selected connectivity path.
5. Configure route tables, firewall rules, NSGs and security policies.
6. Ensure DNS resolution, database access controls, encryption and monitoring.
7. Test connectivity, failover and recovery procedures.

### Interview-ready answer

"I would recommend a Hybrid Cloud deployment model because it combines our existing on-premises infrastructure with OCI public cloud services. We can deploy the application on Oracle Kubernetes Engine while keeping the production database in our on-premises data center. To establish connectivity, we can use Site-to-Site VPN or OCI FastConnect, with a Dynamic Routing Gateway connecting the OCI VCN to the on-premises network. We would also configure appropriate routing, firewall rules and security policies to ensure that the application communicates securely with the database."

**Key takeaway:** Deployment models describe how cloud environments are arranged and connected. The right model depends on business needs, regulatory requirements, existing infrastructure, security, cost and operational capabilities.
