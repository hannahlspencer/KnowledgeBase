# Microsoft Azure

### Azure hierarchy of organisation

Management groups -> subscriptions -> resource groups -> resources

From bottom up:

* **Resources** - instances of services you create eg. virtual machines, SQL databases
* **Resource groups** - resources are combined into resource groups which act as a logical container that Azure resources, like web apps and databases, are deployed into and managed
* **Subscriptions** - A subscription groups user accounts and resources created by those user accounts
* **Management groups** - These help manage access, policy, and compliance

Resources are created in regions, which represent specific datacentres. A region is a geographical area that contains one or more datacentres linked in a low-latency network.

Global regions provide better scalability and redundancy.

### Azure region pairs

Each Azure region is paired with another within the same geography (eg. US, Europe) but at least 300 miles away. This is to prevent interruptions caused by natural disasters, power outages, or similar. If a region in a pair is affected services automatically failover to the other region in its pair.

### Azure resource groups

These are a logical container for resources deployed on Azure. All resources must be in a resource group, and a resource can only be a member of a single resource groups.

Placing resources of similar usage, type, or location into resource groups helps provide order to them.

If you delete a resource group, all of its resources are also deleted.

Resource groups are also a scope for applying role-based access control permissions.

### Azure Resource Manager

This is the deployment and management service for Azure. It provides a management layer to help you create, update, and delete resources.

When a user sends a request from any Azure tool, API or SDK, the Resource Manager receives the request, authenticates and authorises it, and sends it to the Azure service to complete.

A Resource Manager allows you to manage your infrastructure through declarative templates rather than scripts.



### Azure subscriptions

Using Azure requires an Azure subscription, which gives you authenticated and authorised access to Azure products and services.

An Azure subscription is a logical unit of Azure services that links to an Azure account, which is an identity in Azure Active Directory (Azure AD) or in a directory that Azure AD trusts.

An account can have one or more subscriptions that have different billing models and access management policies. Two types of subscription boundary:

* **Billing boundary** - determines how an Azure account is billed for using Azure.
* **Access control boundary** - applies access-management policies at the subscription level, and can create separate subscriptions to reflect different organisational structures.

You might want to create additional subscriptions to separate:

* **Environments** - when managing resources you can choose to create subscriptions to set up separate environments for development and testing, security, or to isolate data for compliance reasons.
* **Organisational structures** - eg. you can limit a team to lower-cost resources while allowing IT the full range. This allows you to manage and control access to the resources that users provision within each subscription.
* **Billing** - As costs are aggregated at the subscription level, subscriptions can manage and track costs based on need.
* **Subscription limits** - subscriptions are bound to some hard limits eg. The max number of Azure ExpressRoute circuits per subscriptions is 10

If an organisation has many subscriptions, Azure management groups provide a level of scope above subscriptions. Subscriptions get organised into containers called management groups, and you can apply your governance conditions to the management groups, where all subscriptions will automatically inherit the conditions applied to the management group.

eg. you can apply policies to a management group that limits the regions available for VM creation, which would then apply to all management groups, subscriptions, and resources under that group.

Things to remember:

1. A management group tree can support up to six levels of depth, not including the root level
2. Each management group and subsciprtion can support only one parents
3. Each management group can have many children
4. All subscriptions and management groups are within a single hierarcy

#### Links

* [Azure Attack Paths](https://cloudbrothers.info/azure-attack-paths/)
