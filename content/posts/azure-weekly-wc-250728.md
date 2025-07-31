+++
title = 'Azure Snippets w/c 28/07/2025'
date = 2025-08-01T08:00:16+01:00
draft = true
categories = ['Azure Weekly 2025']
tags = ['DB for PostgreSQL', 'Redis', 'IaC', 'NSG', 'Application Gateway', 'Azure Backup', 'Virtual Network Manager', 'Compute', 'FinOps', 'Azure Storage']
+++

Summary of Azure snippets for the week commencing 28th July 2025, grouped by Azure service. No major annoucements since my last post, but there have been a number of smaller ones of interest to users of specific services.

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [Application Gateway](#application-gateway)
- [Azure Backup](#azure-backup)
- [Azure Cache for Redis](#azure-cache-for-redis)
- [Azure DB for PostgreSQL](#azure-db-for-postgresql)
- [Azure Kubernetes Service](#azure-kubernetes-service)
- [Infrastructure as Code](#infrastructure-as-code)
- [Network Security Groups](#network-security-groups)
- [Virtual Network Manager](#virtual-network-manager)

## Infrastructure as Code

- [Bicep templates support for Microsoft Entra ID resources (GA)](https://techcommunity.microsoft.com/blog/azuregovernanceandmanagementblog/announcing-ga-of-bicep-templates-support-for-microsoft-entra-id-resources/4437163) : You can now create [Bicep templates](https://learn.microsoft.com/en-us/graph/templates/bicep/) to deploy Entra ID resources such as groups, applications and security principals (e.g. users or service accounts) using Microsoft Graph, supported by the Microsoft Graph for Bicep extension. Entra ID resources can now be created as part of your Azure IaC deployments, rather than having to be done separately using Graph Powershell. This is a powerful update to widen the scope of resources that can be created using Bicep - and since this is an extension for Microsoft Graph (with Entra ID resources being the first supported), support for other Graph resources may come in in the future. (Terraform also has a [resource provider](https://registry.terraform.io/providers/hashicorp/azuread/latest) that can manage Entra ID resources - interestingly though, while the provider is up-to-date, they haven't updated its name and still refer to it as Azure AD!)
