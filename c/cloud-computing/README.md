# Cloud Computing

There are three deployment models for cloud computing:

1. **Public cloud**&#x20;

Services are offered over the public internet and available to anyone who wants to purchase them. Cloud resources, such as servers and storage, are owned and operated by a third-party cloud provider, and delivered over the internet.

On public cloud, organisations only pay for what they use.

**2. Private cloud**&#x20;

This consists of computing resources used only by users from one organisation. It can be physically located at the organisation's on-site datacentre, or can be hosted by a third-party.

On private, organisations must purchase hardware, but have complete control over resources and security.

**3. Hybrid cloud**&#x20;

This combines public and private cloud by allowing data and applications to be shared between them. This provides the most flexibility and organisations can determine where to run their applications.

### Advantages of cloud computing

* **High availability** - Can provide a continuous user experience with no apparent down time
* **Scalability** - Apps can scale horizontally (by adding instances of resources such as VMs) and vertically (by adding RAM or CPUs to a virtual machine)
* **Elasticity** - Can configure cloud-based apps to take advantage of autoscaling so the apps always have the resources they need
* **Agility** - Deployment and configuration of cloud-based resources is fast
* **Geo-distribution** - Can deploy apps to datacentres around the globe ensuring customers always have the best performance for their region
* **Disaster recovery** - Cloud-based backup services, data replication, and geo-distribution protects from disaster

### Cloud service models

#### IaaS aka. Infrastructure-as-a-Service

This model is the closest to physical servers - a cloud provider keeps the hardware up to date, but OS maintenance and network config is up to the tenant.

Basically instead of buying hardware the tenant is renting it, and only paying for what they use.

#### PaaS aka. Platform-as-a-Service&#x20;

This is a managed hosting environment. The cloud provider manages the virtual machines and networking resources, and the tenant deploys their applications into the managed hosting environment

#### SaaS aka. Software-as-a-Service&#x20;

This is where the cloud provider manages all aspects of the application environment such as virtual machines, networking, data storage, and applications. The tenant only needs to provide their data to the application managed by the provider eg. Microsoft Office.

### Serverless computing&#x20;

Eliminates need to manage infrastructure - the cloud service provider automatically provisions, scales, and manages the infrastructure to run the code. Serverless architectures are highly scalable and event-driven, only using resources when a certain trigger occurs.

Servers are still running the code, but it's called serverless as these servers are invisible to the developer.
