### Control access to cloud resources by using Azure role-based access control
When you have multiple IT and engineering teams, how can you control what access they have to the resources in your cloud environment? It's a good security practice to grant users only the rights they need to perform their job, and only to the relevant resources.

Instead of defining the detailed access requirements for each individual, and then updating access requirements when new resources are created, Azure enables you to control access through Azure role-based access control (Azure RBAC).

Azure provides built-in roles that describe common access rules for cloud resources. You can also define your own roles. Each role has an associated set of access permissions that relate to that role. When you assign individuals or groups to one or more roles, they receive all of the associated access permissions.

#### How is role-based access control applied to resources?
Role-based access control is applied to a scope, which is a resource or set of resources that this access applies to.

Here's a diagram that shows the relationship between roles and scopes.  
<img src="https://learn.microsoft.com/en-us/training/azure-fundamentals/build-cloud-governance-strategy-azure/media/4-role-scope-0223bfae.png">  

Scopes include:

A management group (a collection of multiple subscriptions).
A single subscription.
A resource group.
A single resource.

Observers, Users managing resources, Admins, and Automated processes illustrate the kinds of users or accounts that would typically be assigned each of the various roles.

When you grant access at a parent scope, those permissions are inherited by all child scopes. For example:

When you assign the Owner role to a user at the management group scope, that user can manage everything in all subscriptions within the management group.
When you assign the Reader role to a group at the subscription scope, the members of that group can view every resource group and resource within the subscription.
When you assign the Contributor role to an application at the resource group scope, the application can manage resources of all types within that resource group, but not other resource groups within the subscription.

#### How is Azure RBAC enforced?
Azure RBAC is enforced on any action that's initiated against an Azure resource that passes through Azure Resource Manager. Resource Manager is a management service that provides a way to organize and secure your cloud resources.

You typically access Resource Manager from the Azure portal, Azure Cloud Shell, Azure PowerShell, and the Azure CLI. Azure RBAC doesn't enforce access permissions at the application or data level. Application security must be handled by your application.

RBAC uses an allow model. When you're assigned a role, RBAC allows you to perform certain actions, such as read, write, or delete. If one role assignment grants you read permissions to a resource group and a different role assignment grants you write permissions to the same resource group, you have both read and write permissions on that resource group

#### Who does Azure RBAC apply to?
You can apply Azure RBAC to an individual person or to a group. You can also apply Azure RBAC to other special identity types, such as service principals and managed identities. These identity types are used by applications and services to automate access to Azure resources.

Tailwind Traders has the following teams with an interest in some part of their overall IT environment:

IT Administrators This team has ultimate ownership of technology assets, both on-premises and in the cloud. The team requires full control of all resources.
Backup and Disaster Recovery This team is responsible for managing the health of regular backups and invoking any data or system recoveries.
Cost and Billing People in this team track and report on technology-related spend. They also manage the organization's internal budgets.
Security Operations This team monitors and responds to any technology-related security incidents. The team requires ongoing access to log files and security alerts.

#### How do I manage Azure RBAC permissions?
You manage access permissions on the Access control (IAM) pane in the Azure portal. This pane shows who has access to what scope and what roles apply. You can also grant or remove access from this pane.

The following screenshot shows an example of the Access control (IAM) pane for a resource group. In this example, Alain Charon has been assigned the Backup Operator role for this resource group.  
<img src="https://learn.microsoft.com/en-us/training/azure-fundamentals/build-cloud-governance-strategy-azure/media/4-role-based-access-control-blade-360b5130.png"> 

#### How do I manage resource locks?
You can manage resource locks from the Azure portal, PowerShell, the Azure CLI, or from an Azure Resource Manager template.

To view, add, or delete locks in the Azure portal, go to the Settings section of any resource's Locks pane in the Azure portal.

Here's an example that shows how to add a resource lock from the Azure portal. You'll apply a similar resource lock in the next part.

<img src="https://learn.microsoft.com/en-us/training/azure-fundamentals/build-cloud-governance-strategy-azure/media/7-portal-add-lock-ebc3d24c.png">







