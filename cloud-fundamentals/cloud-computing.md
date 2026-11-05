# Cloud Computing

## 1. What is Cloud Computing?

Cloud Computing is the on-demand delivery of computing resources such as
servers, storage, networking, databases and software over a network
(usually the internet), typically with pay-as-you-go pricing.

Instead of purchasing and maintaining physical infrastructure in their
own data center, organizations can provision resources from a cloud
provider whenever they need them.

Examples of cloud providers:

-   Oracle Cloud Infrastructure (OCI)
-   Amazon Web Services (AWS)
-   Microsoft Azure
-   Google Cloud Platform (GCP)

## 2. Why Do We Need Cloud Computing?

Traditionally, an organization hosting an application had to purchase
physical servers, networking equipment and storage, arrange a data
center, install operating systems, and maintain the hardware.

This involved significant upfront investment, procurement time and
ongoing operational effort.

Cloud computing provides an alternative: organizations can rent
computing resources on demand and let the cloud provider manage the
underlying physical infrastructure.

## 3. Traditional Data Center vs Cloud Computing

  -----------------------------------------------------------------------
  Traditional Data Center             Cloud Computing
  ----------------------------------- -----------------------------------
  Organization purchases physical     Organization provisions cloud
  servers                             resources

  High upfront capital investment     Usually lower upfront investment

  Organization maintains physical     Cloud provider manages the physical
  hardware                            infrastructure

  Capacity must often be planned in   Resources can be provisioned and
  advance                             adjusted on demand

  Hardware procurement can take time  Provisioning can be much faster

  Organization operates its own data  Infrastructure is provided through
  center                              a cloud service
  -----------------------------------------------------------------------

**Important:** Cloud computing does not eliminate physical data centers.
Cloud providers operate large physical data centers containing servers,
storage and networking equipment. They abstract and manage this
infrastructure to deliver services to customers.

## 4. How Does Cloud Computing Work?

A simplified view of the process:

1.  A cloud provider operates physical data centers.
2.  Physical servers provide CPU, memory, storage and network capacity.
3.  Virtualization and cloud-management systems make infrastructure
    resources available to customers.
4.  A customer requests resources through a web console, CLI, API or
    Infrastructure as Code.
5.  The cloud platform provisions the requested resources.
6.  The customer configures the operating system, application and
    workload, depending on the service model.

For a virtual machine, the simplified relationship is:

``` text
Physical Data Center
        |
Physical Server
        |
Virtualization Layer / Hypervisor
        |
Virtual Machine
        |
Operating System
        |
Application
```

The exact implementation varies by cloud service and instance type. Not
every cloud compute service is necessarily a conventional virtual
machine.

## 5. Key Benefits of Cloud Computing

### 5.1 Scalability

Scalability is the ability to increase or decrease resources to handle
changing workload requirements.

For example, an organization can add application instances or increase
compute capacity when user traffic grows.

### 5.2 Elasticity

Elasticity is the ability to adjust resources dynamically as demand
changes.

For example, an application can scale out during a traffic spike and
scale in when demand decreases.

### 5.3 Cost Optimization

Cloud services can reduce the need for large upfront hardware purchases.
Many services use consumption-based pricing, although the actual cost
depends on resource usage, service type, configuration and pricing
model.

Cloud resources still require budgeting, monitoring and cost governance.

### 5.4 High Availability

High Availability (HA) is the design of systems to minimize service
interruption.

It can involve redundant resources, multiple failure domains, load
balancing, health checks and automated failover.

**Cloud does not automatically guarantee zero downtime.** Availability
depends on the architecture, service guarantees, configuration and
operational practices.

### 5.5 Disaster Recovery

Disaster Recovery (DR) is the ability to restore services after a major
failure or disruption.

Cloud platforms provide capabilities such as backups, replication and
deployment across regions. A DR solution must still be designed, tested
and maintained.

Two important DR terms:

-   **RPO (Recovery Point Objective):** The maximum acceptable amount of
    data loss, measured in time.
-   **RTO (Recovery Time Objective):** The target time to restore a
    service after disruption.

### 5.6 Global Reach

Cloud providers operate infrastructure in multiple geographic regions.
Organizations can deploy workloads closer to users or across regions for
resilience.

Global availability is not automatic; it requires appropriate
deployment, networking, DNS and application architecture.

### 5.7 Automation

Cloud resources can be created and managed through APIs, CLI tools and
Infrastructure as Code (IaC), such as Terraform.

Automation improves consistency, repeatability and deployment speed.

## 6. Real-World Example: Migrating an Application to OCI

Imagine an organization runs a web application on three physical servers
in its own data center. Traffic is increasing, and maintaining hardware
is becoming expensive.

The organization plans to migrate the application to Oracle Cloud
Infrastructure (OCI).

A simplified migration approach:

1.  Assess the existing application, dependencies, data and capacity
    requirements.
2.  Design the target OCI architecture.
3.  Create the required network infrastructure using a Virtual Cloud
    Network (VCN), subnets, route tables and security rules.
4.  Provision suitable compute resources or a managed platform.
5.  Migrate application components and data.
6.  Configure load balancing, monitoring, backups and security.
7.  Test performance, availability and recovery.
8.  Cut over traffic after validating the new environment.

Potential benefits:

-   Reduced physical hardware maintenance.
-   Faster infrastructure provisioning.
-   Flexible capacity as traffic changes.
-   Better opportunities for automation.
-   Access to cloud backup, replication and recovery capabilities.
-   Ability to deploy in multiple OCI regions where required.

The migration must be planned carefully. Cloud adoption does not
automatically make an application cheaper, highly available or globally
accessible.

## 7. Connection with Kubernetes and OKE

Kubernetes manages containerized workloads, but those workloads still
need underlying infrastructure.

In Oracle Kubernetes Engine (OKE):

-   OCI provides the underlying cloud infrastructure.
-   OCI Compute provides worker-node infrastructure for managed node
    pools.
-   VCN provides network connectivity.
-   OCI Load Balancer can expose applications.
-   OCI Block Volume and File Storage can provide persistent storage.
-   OKE provides a managed Kubernetes control plane and integrates
    Kubernetes with OCI services.

This is why understanding OCI fundamentals is valuable before going
deeper into OKE.

## 8. Important Cloud Terminology

  -----------------------------------------------------------------------
  Term                                Meaning
  ----------------------------------- -----------------------------------
  Cloud Provider                      Organization that offers cloud
                                      services

  Region                              Geographic area containing cloud
                                      infrastructure

  Availability Domain                 Isolated data-center grouping in
                                      OCI regions that have multiple ADs

  Fault Domain                        Hardware and infrastructure
                                      grouping designed to limit
                                      correlated failures within an
                                      Availability Domain

  Virtualization                      Technology that allows logical
                                      computing resources to share
                                      physical infrastructure

  Hypervisor                          Software or firmware layer that
                                      creates and manages virtual
                                      machines

  Scalability                         Ability to increase or decrease
                                      capacity

  Elasticity                          Ability to adjust capacity
                                      dynamically with demand

  High Availability                   Architecture designed to minimize
                                      service interruption

  Disaster Recovery                   Processes and systems used to
                                      restore services after disruption

  Pay-as-you-go                       Pricing based on consumption,
                                      subject to service-specific pricing
                                      rules
  -----------------------------------------------------------------------

## 9. Interview Questions and Answers

### Q1. What is Cloud Computing?

Cloud Computing is the on-demand delivery of computing resources such as
compute, storage, networking and databases over a network, typically
with consumption-based pricing.

### Q2. What is the difference between traditional infrastructure and cloud infrastructure?

Traditional infrastructure generally requires organizations to purchase
and maintain physical hardware. Cloud infrastructure allows
organizations to provision computing resources from a cloud provider
without directly owning and operating the underlying physical
infrastructure.

### Q3. Does cloud computing eliminate physical data centers?

No. Cloud providers operate physical data centers containing servers,
storage and networking equipment. They use infrastructure management,
virtualization and automation to deliver cloud services.

### Q4. Why do companies migrate applications to the cloud?

Common reasons include faster provisioning, flexible capacity,
automation, global deployment options, access to managed services and
opportunities to optimize infrastructure costs.

### Q5. Does running an application in the cloud guarantee zero downtime?

No. Cloud platforms provide capabilities to build highly available
systems, but the customer must design for redundancy, health checks,
load balancing, backups and failover. Application bugs, configuration
errors and regional disruptions can still cause downtime.

### Q6. What is the difference between scalability and elasticity?

Scalability is the ability to increase or decrease system capacity.
Elasticity is the ability to adjust that capacity dynamically in
response to changing demand.

### Q7. What is the difference between High Availability and Disaster Recovery?

High Availability focuses on minimizing service interruption during
component failures. Disaster Recovery focuses on restoring services
after a major disruption, such as a regional outage or data-center
disaster.

## 10. Practical Exercise

**Scenario:** An organization runs a web application on three physical
servers in its own data center. Traffic is growing, and hardware
maintenance is becoming expensive. The organization wants to migrate the
application to OCI.

Answer these questions:

1.  What infrastructure does the organization currently own?
2.  Which OCI services could replace or support its existing
    infrastructure?
3.  Where would the application run?
4.  How would users access the application?
5.  How could the organization improve availability and disaster
    recovery?
6.  What cost and security risks should be considered during migration?

No paid OCI resources are required for this conceptual exercise.
