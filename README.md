# Enterprise Scale Landing Zone

Azure landing zones are the output of a multisubscription Azure environment that accounts for scale, security governance, networking, and identity. Azure landing zones enable application migration, modernization, and innovation at enterprise-scale in Azure. These zones consider all platform resources that are required to support the customer's application portfolio and don't differentiate between infrastructure as a service or platform as a service.

![alt image](https://github.com/DavidArayaSanabria/Azure-Landing-Zone-Accelerator/blob/4eebf9894a8e203c31cb1d664fc13552c84cd789/Images/image%201.png)


# Scalable and modular
No single solution fits all technical environments. A few Azure landing zone implementation options can help you meet the deployment and operations needs of your growing cloud portfolio.

## Scalable: 

All Azure landing zones support cloud adoption at scale by providing repeatable environments, with consistent configuration and controls, regardless of the workloads or Azure resources deployed to each landing zone instance.
## Modular:
All Azure landing zones provide a modular approach to building out your environment, based on a common set of design areas. Each design area can be easily extended to support the distinct needs of various technology platforms like Azure SQL Database, Azure Kubernetes Service, and Azure Virtual Desktop.

Whether you're looking to deploy your first production application to Azure or you're operating a complex portfolio of tech platforms and workloads, the Azure landing zone implementation options can be tailored to your needs.

## Target audience

- Infrastructure Teams
- Security Teams
- Network Administrators
- Cloud Solution Architect
- Financial Team
- Project Managers

# Azure landing zone conceptual architecture
For many organizations, the Azure landing zone conceptual architecture below represents the destination in their cloud adoption journey. It's a mature, scaled-out target architecture intended to help organizations operate successful cloud environments that drive their business while maintaining best practices for security and governance.

This conceptual architecture represents scale and mature decisions based on a wealth of lessons learned and feedback from customers who have adopted Azure as part of their digital estate.

![alt image](https://github.com/DavidArayaSanabria/Azure-Landing-Zone-Accelerator/blob/4eebf9894a8e203c31cb1d664fc13552c84cd789/Images/image%202.png)


# Azure landing zone accelerator

The accelerator is an Azure-portal-based deployment that will provide a full implementation of the conceptual architecture, along with opinionated configurations for key components such as management groups and policies.

# Prerequisites for deploying using the Azure landing zone accelerator

## Define with your Team and Cloud Architect how many and the purpose of the subscriptions you   will need and create them. Subscriptions can be a single one or several subscriptions in an Enterprise Agreement for different purposes, for example:

- Management subscription (Used for Logs, Key Vaults, Monitoring services, etc)
- Connectivity subscription (Used for Firewalls, Virtual Networks, Gateways, VPNs, etc)
- Identity subscription (Domain Controllers in the cloud)


## Define if your Azure AD used for Office 365 will be used also for the new Azure environment.

## Deploying the Azure landing zone accelerator requires permissions for creating resources at the tenant (/) scope. 

As a Global Administrator in Azure Active Directory (Azure AD), you might not have access to all subscriptions and management groups in your directory.

Why would you need to elevate your access?
If you are a Global Administrator, there might be times when you want to do the following actions:

- Regain access to an Azure subscription or management group when a user has lost access
- Grant another user or you access to an Azure subscription or management group
- See all Azure subscriptions or management groups in an organization
- Allow an automation app (such as an invoicing or auditing app) to access all Azure subscriptions or management groups

How does elevated access work?
Azure AD and Azure resources are secured independently from one another. That is, Azure AD role assignments do not grant access to Azure resources, and Azure role assignments do not grant access to Azure AD. However, if you are a Global Administrator in Azure AD, you can assign yourself access to all Azure subscriptions and management groups in your directory. Use this capability if you don't have access to Azure subscription resources, such as virtual machines or storage accounts, and you want to use your Global Administrator privilege to gain access to those resources.

When you elevate your access, you will be assigned the User Access Administrator role in Azure at root scope (/). This allows you to view all resources and assign access in any subscription or management group in the directory. User Access Administrator role assignments can be removed using Azure PowerShell, Azure CLI, or the REST API.

You should remove this elevated access once you have made the changes you need to make at root scope.

![alt image](https://github.com/DavidArayaSanabria/Azure-Landing-Zone-Accelerator/blob/d550c0e5f03f58856f06abc2f5ce6f79084a0712/Images/image%203.png)

# Elevate access for a Global Administrator
Follow these steps to elevate access for a Global Administrator using the Azure portal.

Sign into the Azure portal or the Azure Active Directory admin center as a Global Administrator.

If you are using Azure AD Privileged Identity Management, activate your Global Administrator role assignment.

Open Azure Active Directory.

Under Manage, select Properties.

![alt image](https://github.com/DavidArayaSanabria/Azure-Landing-Zone-Accelerator/blob/d550c0e5f03f58856f06abc2f5ce6f79084a0712/Images/Image%204.png)


Under Access management for Azure resources, set the toggle to Yes.

![alt image](https://github.com/DavidArayaSanabria/Azure-Landing-Zone-Accelerator/blob/4eebf9894a8e203c31cb1d664fc13552c84cd789/Images/Image%205.png)

When you set the toggle to Yes, you are assigned the User Access Administrator role in Azure RBAC at root scope (/). This grants you permission to assign roles in all Azure subscriptions and management groups associated with this Azure AD directory. This toggle is only available to users who are assigned the Global Administrator role in Azure AD.

Click Save to save your setting.

This setting is not a global property and applies only to the currently signed in user. You can't elevate access for all members of the Global Administrator role.

Sign out and sign back in to refresh your access.

![alt image](https://github.com/DavidArayaSanabria/Azure-Landing-Zone-Accelerator/blob/4eebf9894a8e203c31cb1d664fc13552c84cd789/Images/Image%206.png)


Elevate account access so the Global Administrator can assign roles.

Assign Owner or Contributor to the principal that needs to deploy the templates.

Azure CLI:

```
az ad signed-in-user show 
az role assignment create --scope '/' --role 'Owner' --assignee-object-id <id> --assignee-principal-type User
```
## Run the Landing Zone Accelerator

With the assistance of your key Team members involved on this project and the  Microsoft folks fill out the Landing Zone Accelerator template using the button below

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://aka.ms/caf/ready/accelerator)


![alt image](https://github.com/DavidArayaSanabria/Azure-Landing-Zone-Accelerator/blob/d550c0e5f03f58856f06abc2f5ce6f79084a0712/Images/image%207.png)


## Azure services and related products

- Cloud Adoption Framework
- Azure CLI
- ARM Templates
- Azure Active Directory

## Related references
- https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/ready/landing-zone/
- https://docs.microsoft.com/en-us/azure/role-based-access-control/elevate-access-global-admin?WT.mc_id=Portal-Microsoft_Azure_CreateUIDef
- https://github.com/Azure/Enterprise-Scale/blob/main/docs/EnterpriseScale-Setup-azure.md



