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
