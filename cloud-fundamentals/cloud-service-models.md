# Cloud Service Models – IaaS, PaaS, SaaS and FaaS

## 1. What are Cloud Service Models?

Cloud service models describe how cloud services are delivered and how responsibilities are divided between the cloud provider and the customer.

The four commonly discussed models are:
- **IaaS – Infrastructure as a Service**
- **PaaS – Platform as a Service**
- **SaaS – Software as a Service**
- **FaaS – Function as a Service**

The more managed the service is, the less underlying infrastructure the customer usually needs to operate. However, customers still have responsibilities, especially around identity, access, data and configuration.

## 2. IaaS – Infrastructure as a Service

IaaS provides computing resources such as virtual machines, storage and networking over the cloud. The provider manages the physical infrastructure and virtualization layer. The customer manages the guest operating system, installed software, runtime, applications and data.

### Typical responsibilities

| Component | Responsible party |
|---|---|
| Physical data center and hardware | Cloud provider |
| Physical networking and virtualization | Cloud provider |
| VM configuration | Shared / customer configures it |
| Guest operating system | Customer |
| Middleware and runtime | Customer |
| Application and data | Customer |

### OCI examples
- **OCI Compute:** Create and manage virtual machines or use bare metal compute.
- **OCI Block Volume:** Attach persistent block storage to compute instances.
- **OCI Virtual Cloud Network (VCN):** Configure cloud networking, subnets, route tables and security rules.

**Practical example:** A team creates an Ubuntu VM in OCI, installs Nginx and Docker, configures firewall rules, and deploys an application. This is an IaaS-style workload because the team manages the guest OS and software stack.

**When to use IaaS:** When you need OS-level control, custom software, flexibility over infrastructure, or a straightforward migration path for an existing VM-based application.

## 3. PaaS – Platform as a Service

PaaS provides a managed application platform. The provider manages the underlying infrastructure and platform components, such as the operating system and supported runtime. Developers focus primarily on application code and data.

### Typical responsibilities

| Component | Responsible party |
|---|---|
| Physical infrastructure and virtualization | Cloud provider |
| Operating system | Cloud provider |
| Managed runtime / platform | Cloud provider |
| Application code | Customer |
| Application data and configuration | Customer |

### OCI examples
- **Oracle Autonomous Database:** A managed database service that automates many database administration tasks.
- **Oracle Functions:** A serverless function service; more specifically, this is FaaS.
- Other OCI managed application and database services can provide PaaS-like capabilities depending on the workload.

**Practical example:** A development team deploys an application to a managed application platform without provisioning VMs or maintaining the guest operating system and runtime. The team concentrates on application development and deployment.

**When to use PaaS:** When developers want to focus on application code, reduce OS/runtime administration, and can use the supported managed platform.

## 4. SaaS – Software as a Service

SaaS provides ready-to-use software over the internet. Users access the application through a browser, mobile app or API. The provider operates the application and its underlying platform and infrastructure. Customers still manage users, access permissions, data handling and service configuration.

### Typical responsibilities

| Component | Responsible party |
|---|---|
| Physical infrastructure, OS and runtime | Cloud provider |
| Application software | Cloud provider |
| User access and permissions | Customer |
| Customer data and usage configuration | Shared, depending on the service |

### Examples
- Gmail
- Microsoft 365
- Salesforce
- Oracle Fusion Cloud Applications

**Practical example:** An organization uses Microsoft 365 for email and document collaboration. It does not build or maintain its own email servers; employees simply use the service. Administrators still manage accounts, access and organizational settings.

**When to use SaaS:** When you need a ready-made business application and do not want to develop or host it yourself.

## 5. FaaS – Function as a Service

FaaS allows developers to run individual pieces of code, called functions, without managing the underlying execution servers. Functions are commonly triggered by events or requests.

FaaS is commonly associated with serverless computing. Serverless is a broader concept; not every serverless service is FaaS.

### How FaaS works: image-processing example

1. A user uploads an image to an Object Storage bucket.
2. An event is generated.
3. The event triggers a function.
4. The function processes the image.
5. The result is stored or sent to another service.

**OCI example:** Oracle Functions is OCI's serverless functions service. Other examples include AWS Lambda and Azure Functions.

**When to use FaaS:** When a task should run in response to an event, can be expressed as an independent function, and fits the function service's execution limits and model.

## 6. Comparison of IaaS, PaaS, SaaS and FaaS

| Feature | IaaS | PaaS | SaaS | FaaS |
|---|---|---|---|---|
| Main offering | Infrastructure | Managed platform | Ready-to-use software | Function execution |
| Infrastructure management | Provider | Provider | Provider | Provider |
| OS management | Customer | Provider | Provider | Provider |
| Runtime management | Customer | Provider | Provider | Provider |
| Application code | Customer | Customer | Provider operates it | Customer |
| Customer's main focus | Infrastructure and workload | Application development | Using the software | Function logic |
| Typical control | High | Medium | Lower | Function-level |

**Easy way to remember:**
- IaaS: Rent the infrastructure.
- PaaS: Use a ready platform.
- SaaS: Use ready software.
- FaaS: Run code when triggered.

These are simplified categories. Real cloud services can combine characteristics from more than one model.

## 7. Shared Responsibility Model

The shared responsibility model explains how security and operational responsibilities are divided between a cloud provider and its customer.

Moving workloads to the cloud does not mean the provider becomes responsible for everything. The provider secures the cloud infrastructure it operates. The customer remains responsible for securing workloads, identities, data and configurations according to the service being used.

### Simplified responsibility comparison

| Responsibility | IaaS | PaaS | SaaS |
|---|---|---|---|
| Physical data center | Provider | Provider | Provider |
| Physical hardware | Provider | Provider | Provider |
| Underlying network infrastructure | Provider | Provider | Provider |
| Guest operating system | Customer | Provider | Provider |
| Middleware / runtime | Customer | Provider | Provider |
| Application software | Customer | Customer | Provider |
| Customer data | Customer | Customer | Shared responsibilities |
| User access configuration | Customer | Customer | Customer |

This table is a learning aid, not a universal contractual responsibility matrix. Always check the responsibility documentation for the specific cloud service.

### OCI Compute security example

Suppose an application runs on an OCI Compute VM.

**Oracle generally manages:** physical data center security, physical server security, underlying cloud infrastructure and the virtualization infrastructure used by the service.

**The customer generally manages:** guest OS patching and hardening, SSH access and credentials, application security patches, application secrets, workload access permissions, security rules and network configuration they create, and appropriate protection of application data.

**Interview point:** The cloud provider secures the cloud infrastructure, while the customer is responsible for securing workloads and configurations in the cloud. The exact responsibility boundary changes with the service model.

## 8. Connecting Service Models to Kubernetes and OKE

Oracle Kubernetes Engine (OKE) is a managed Kubernetes service. It should not be described as simply a traditional PaaS or FaaS offering.

OCI manages the Kubernetes control plane for OKE, while customers remain responsible for their workloads and many cluster and network configurations.

| Component | Typical responsibility |
|---|---|
| Physical OCI infrastructure | Oracle |
| Managed OKE control plane | Oracle |
| Node pool and worker-node configuration | Customer-managed configuration; details depend on node type |
| Kubernetes deployments and workloads | Customer |
| Container images and application code | Customer |
| Kubernetes RBAC and workload configuration | Customer |
| OCI networking and security configuration | Shared according to service boundaries |

### Different node approaches
- **Managed nodes:** The customer configures node pools and workloads. Oracle manages the OKE control plane; node OS and lifecycle responsibilities depend on the service capabilities and configuration.
- **Virtual nodes:** More worker-node infrastructure is abstracted away, reducing node administration.
- **Self-managed Kubernetes on OCI Compute:** The customer takes on substantially more responsibility, including operating the Kubernetes control plane and worker nodes.

OKE is best described as a managed Kubernetes service with shared operational responsibilities, rather than simply calling it a traditional PaaS.

## 9. Choosing the Right Service Model

| Requirement | Suitable model | Reason |
|---|---|---|
| Create an Ubuntu VM and install Docker | IaaS | The team manages the OS and software stack |
| Deploy an application without managing servers or runtime | PaaS | The provider manages the application platform |
| Use ready-made email or office software | SaaS | The organization consumes existing software |
| Run code when an object is uploaded | FaaS | An event triggers a function |

There is no universally best model. Choose based on required control, flexibility, operational effort, security needs, workload compatibility and cost.

## 10. Real-World Scenario

**Scenario:** A company currently runs applications on OCI Compute VMs. Management wants to reduce server administration and let developers focus more on application development.

**Recommended direction:** Consider PaaS or an appropriate managed application platform.

**Reason:** The provider can manage more of the underlying infrastructure, operating system and supported runtime, reducing administration overhead. Developers can focus more on application code and delivery.

The exact service should be selected after checking application compatibility, required control, security, availability, performance and pricing.

### Interview-ready answer

"I would recommend the PaaS model because it reduces the operational overhead of managing infrastructure, operating systems and application runtimes. The cloud provider manages the underlying platform, allowing our development team to focus more on writing, deploying and maintaining application code. This can improve developer productivity and reduce infrastructure administration effort."

## 11. Interview Questions and Answers

### Q1. What is the difference between IaaS, PaaS and SaaS?

IaaS provides infrastructure such as virtual machines, storage and networking. PaaS provides a managed application platform, while SaaS provides ready-to-use software over the internet.

### Q2. Is OCI Compute IaaS or PaaS?

OCI Compute is primarily an IaaS offering because customers manage the guest operating system, software and applications running on the compute instance.

### Q3. Is Oracle Autonomous Database IaaS or PaaS?

It is generally categorized as a managed database platform service, or PaaS. Oracle automates many database administration tasks, while customers still manage their data, schemas and access.

### Q4. What is the difference between FaaS and PaaS?

PaaS provides a managed application platform for deploying and running applications. FaaS executes individual functions in response to events or requests, without requiring customers to manage the execution servers.

### Q5. Does moving to SaaS mean the customer has no security responsibility?

No. The provider manages the application and underlying infrastructure, but customers still need to manage users, access permissions, data handling and security settings.

### Q6. What is the shared responsibility model?

It defines how cloud security responsibilities are divided between the cloud provider and customer. The provider secures the underlying cloud infrastructure, while the customer secures their workloads and configurations according to the service model.

### Q7. Is OKE a PaaS service?

OKE is a managed Kubernetes service. Oracle manages the Kubernetes control plane, but customers still manage workloads and many cluster configurations. It is more accurate to call it a managed Kubernetes service than to classify it as a simple traditional PaaS offering.

## 12. Practical Exercise

For each requirement, identify the suitable cloud service model and explain why.

1. A DevOps team wants to create an Ubuntu VM, install Docker, configure the OS and deploy an application.
2. Developers want to deploy an application without managing servers, OS or runtime.
3. The HR department wants ready-to-use employee management software through a browser.
4. A function should run automatically whenever a file is uploaded to cloud storage.

### Suggested answers

1. **IaaS** – the team manages the VM's operating system and software.
2. **PaaS** – the provider manages the platform while developers deploy their application.
3. **SaaS** – the HR team consumes ready-to-use software.
4. **FaaS** – an event triggers function execution.
