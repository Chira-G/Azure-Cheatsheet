# Overview of Azure 
## subscriptions, management groups, and resources
The following image shows the top-down hierarchy of organization for these levels.
<img src="https://learn.microsoft.com/en-us/training/azure-fundamentals/azure-architecture-fundamentals/media/hierarchy-372fef74.png">  
- Resources: Resources are instances of services that you create, like virtual machines, storage, or SQL databases.  
- Resource groups: Resources are combined into resource groups. Resource groups act as a logical container into which Azure resources like web apps, databases, and storage accounts are deployed and managed.  
- Subscriptions: A subscription groups together user accounts and the resources that have been created by those user accounts. For each subscription, there are limits or quotas on the amount of resources that you can create and use. Organizations can use subscriptions to manage costs and the resources that are created by users, teams, or projects.  
- Management groups: These groups help you manage access, policy, and compliance for multiple subscriptions. All subscriptions in a management group automatically inherit the conditions applied to the management group.

## Azure regions, availability zones, and region pairs.  
- Resources are created in regions, which are different geographical locations around the globe that contain Azure datacenters.  
- Azure is made up of datacenters located around the globe. When you use a service or create a resource such as an SQL database or virtual machine (VM), you're using physical equipment in one or more of these locations. These specific datacenters aren't exposed to users directly. Instead, Azure organizes them into regions. As you'll see later in this unit, some of these regions offer availability zones, which are different Azure datacenters within that region.
### Azure regions
- A region is a geographical area on the planet that contains at least one but potentially multiple datacenters that are nearby and networked together with a low-latency network. Azure intelligently assigns and controls the resources within each region to ensure workloads are appropriately balanced.  
- When you deploy a resource in Azure, you'll often need to choose the region where you want your resource deployed.  
- Some services or VM features are only available in certain regions, such as specific VM sizes or storage types. There are also some global Azure services that don't require you to select a particular region, such as Azure Active Directory, Azure Traffic Manager, and Azure DNS.  
- A few examples of regions are West US, Canada Central, West Europe, Australia East, and Japan West. Here's a view of all the available regions as of June 2020.
<img src="https://learn.microsoft.com/en-us/training/azure-fundamentals/azure-architecture-fundamentals/media/regions-small-be724495.png">    

### Azure availability zones  
You want to ensure your services and data are redundant so you can protect your information if there's a failure. When you host your infrastructure, setting up your own redundancy requires that you create duplicate hardware environments. Azure can help make your app highly available through availability zones.
#### What is an availability zone?
Availability zones are physically separate datacenters within an Azure region. Each availability zone is made up of one or more datacenters equipped with independent power, cooling, and networking. 
An availability zone is set up to be an isolation boundary. If one zone goes down, the other continues working. Availability zones are connected through high-speed, private fiber-optic networks.  
<img src="https://learn.microsoft.com/en-us/training/azure-fundamentals/azure-architecture-fundamentals/media/availability-zones-5c3c490c.png">
## Azure subscriptions  
Using Azure requires an Azure subscription. A subscription provides you with authenticated and authorized access to Azure products and services. It also allows you to provision resources. An Azure subscription is a logical unit of Azure services that links to an Azure account, which is an identity in Azure Active Directory (Azure AD) or in a directory that Azure AD trusts.  
<img src="https://learn.microsoft.com/en-us/training/azure-fundamentals/azure-architecture-fundamentals/media/subscriptions-afe063a7.png">  
An account can have one subscription or multiple subscriptions that have different billing models and to which you apply different access-management policies. You can use Azure subscriptions to define boundaries around Azure products, services, and resources. There are two types of subscription boundaries that you can use:

- Billing boundary: This subscription type determines how an Azure account is billed for using Azure. You can create multiple subscriptions for different types of billing requirements. Azure generates separate billing reports and invoices for each subscription so that you can organize and manage costs.  
- Access control boundary: Azure applies access-management policies at the subscription level, and you can create separate subscriptions to reflect different organizational structures. An example is that within a business, you have different departments to which you apply distinct Azure subscription policies. This billing model allows you to manage and control access to the resources that users create within specific subscriptions.

### Create additional Azure subscriptions  
You might want to create additional subscriptions for resource or billing management purposes. For example, you might choose to create additional subscriptions to separate:  

- Environments: When managing your resources, you can choose to create subscriptions to set up separate environments for development and testing, security, or to isolate data for compliance reasons. This design is particularly useful because resource access control occurs at the subscription level.  
- Organizational structures: You can create subscriptions to reflect different organizational structures. For example, you could limit a team to lower-cost resources, while allowing the IT department a full range. This design allows you to manage and control access to the resources that users create within each subscription.   
- Billing: You might want to also create additional subscriptions for billing purposes. Because costs are first aggregated at the subscription level, you might want to create subscriptions to manage and track costs based on your needs. For instance, you might want to create one subscription for your production workloads and another subscription for your development and testing workloads.  
You might also need additional subscriptions because of:  
- Subscription limits: Subscriptions are bound to some hard limitations. For example, the maximum number of Azure ExpressRoute circuits per subscription is 10. Those limits should be considered as you create subscriptions on your account. If there's a need to go over those limits in particular scenarios, you might need additional subscriptions.  

#### Customize billing to meet your needs
If you have multiple subscriptions, you can organize them into invoice sections. Each invoice section is a line item on the invoice that shows the charges incurred that month. For example, you might need a single invoice for your organization but want to organize charges by department, team, or project.

Depending on your needs, you can set up multiple invoices within the same billing account by creating additional billing profiles. Each billing profile has its own monthly invoice and payment method.

The following diagram shows an overview of how billing is structured. If you've previously signed up for Azure or if your organization has an Enterprise Agreement, your billing might be set up differently.

<img src="https://learn.microsoft.com/en-us/training/azure-fundamentals/azure-architecture-fundamentals/media/billing-structure-overview-2c81a8ad.png">  

## Azure management groups
If your organization has many subscriptions, you might need a way to efficiently manage access, policies, and compliance for those subscriptions. Azure management groups provide a level of scope above subscriptions. You organize subscriptions into containers called management groups and apply your governance conditions to the management groups. All subscriptions within a management group automatically inherit the conditions applied to the management group. Management groups give you enterprise-grade management at a large scale no matter what type of subscriptions you might have. All subscriptions within a single management group must trust the same Azure AD tenant.

For example, you can apply policies to a management group that limits the regions available for VM creation. This policy would be applied to all management groups, subscriptions, and resources under that management group by only allowing VMs to be created in that region.

#### Hierarchy of management groups and subscriptions
You can build a flexible structure of management groups and subscriptions to organize your resources into a hierarchy for unified policy and access management. The following diagram shows an example of creating a hierarchy for governance by using management groups.
<img src="https://learn.microsoft.com/en-us/training/azure-fundamentals/azure-architecture-fundamentals/media/management-groups-and-subscriptions-bba71896.png">  

You can create a hierarchy that applies a policy. For example, you could limit VM locations to the US West Region in a group called Production. This policy will inherit onto all the Enterprise Agreement subscriptions that are descendants of that management group and will apply to all VMs under those subscriptions. This security policy can't be altered by the resource or subscription owner, which allows for improved governance.

Another scenario where you would use management groups is to provide user access to multiple subscriptions. By moving multiple subscriptions under that management group, you can create one role-based access control (RBAC) assignment on the management group, which will inherit that access to all the subscriptions. One assignment on the management group can enable users to have access to everything they need instead of scripting RBAC over different subscriptions.

##### Important facts about management groups
- 10,000 management groups can be supported in a single directory.
- A management group tree can support up to six levels of depth. This limit doesn't include the root level or the subscription level.
- Each management group and subscription can support only one parent.
- Each management group can have many children.
- All subscriptions and management groups are within a single hierarchy in each directory.


