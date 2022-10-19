# Virtual Machines

Azure VMs are a type of on-demand scalable computing resource. They give total control over the configuration and can install anything you need to perform the work. There is no need to purchase physical hardware when scaling or extending the datacentre.

VMs act as normal workstations and servers that act within the bounds of hardware you define for the, IaaS ties these machines into their actual hardware. With VMs you still need to maintain an OS, patches, etc.

All VMs have at least 2 disks - one for the OS, one temporary disk, which will lose all its data when shut down Can add extra disks to persist data VM needs to be attached to a Virtual Network Interface, a private IP and optionally a public IP address. That's how the Azure resources communicate with each other and your networks

All VMs can be organised into a resource group (but don't have to be).

### The Network

Virtual Networks (VNets) are used in Azure to provide private connectivity between Azure VMs and other Azure services. VMs and services that are part of the same virtual network can access one another. Services outside the network cannot connect to services within the network, but you can configure the network to allow access to the external service.

When you set up a virtual network, you specify the address spaces, subnets, and security. If the VNet will connect to other VNets, address ranges can't overlap.

There is no security boundary between subnets, so services in each subnet can talk to each other. However you can set up Network Security Groups (NSGs) which allow you to control the traffic flow to and from subnets and to and from VMs. NSGs act as software firewalls, applying custom rules to each inbound and outbound request at the network interface and subnet level. This allows you to full control every network request in or out of the VM.

After mapping communication and network requirements, take an inventory of:

* Which OS is used?
* How much disk space is in use?
* What kind of data does this use? Are there restrictions on how it's stored or its physical location?
* What sort of CPU, memory, and disk I/O load does the server have?

For the VM name include information: environment (dev, prod), location (eus, jw), instance (01, 02), service, and role (SQL, web) eg. `deveus-webvm01` could be the first development web server hosted in the east US location

VM size - Azure provides different VM sizes that offer variations of power, memory, and storage capacity. If your size needs change you can also upgrade or downgrade the VM size as long as the current hardware configuration is allowed in the new size.
