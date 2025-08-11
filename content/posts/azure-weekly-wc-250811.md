+++
title = 'Azure Snippets w/c 11/08/2025'
date = 2025-08-13T08:00:16+01:00
draft = true
categories = ['Azure Weekly 2025']
tags = ['DB for PostgreSQL', 'Redis', 'IaC', 'NSG', 'Application Gateway', 'Azure Backup', 'Virtual Network Manager', 'Compute', 'FinOps', 'Azure Storage']
+++

Summary of Azure snippets for the week commencing 11th August 2025, grouped by Azure service. Lots of AKS announcements this time, but there are a few other service updates as well (including one that I've personally been waiting a while for!).

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

## Application Gateway

- [Private Application Gateway on Application Gateway v2 (GA)](https://azure.microsoft.com/en-us/updates?id=500225) : I've been waiting for this feature to go GA for more than 2 years now! Finally, [private deployments for the v2 Application Gateway](https://learn.microsoft.com/en-us/azure/application-gateway/application-gateway-private-deployment?tabs=portal) are available. These permit: private IP only frontend configuration (no Public IP address is required for management); enhanced control over Network Security Groups (the GatewayManager inbound rules are no longer needed and you can define a 'Deny All' outbound rule to drop other traffic); and enhanced UDR support (forced tunnelling to a network appliance using the '0.0.0.0/0' rule is now supported).

## Azure Kubernetes Services

- [Deployment safeguards (GA)](https://azure.microsoft.com/en-us/updates?id=499299) : [Deployment Safeguards](https://learn.microsoft.com/en-gb/azure/aks/deployment-safeguards) enforce Kubernetes best practices in your AKS cluster through Azure Policy controls. This looks to be an Azure Policy initiative containing AKS-specific best practice policies, that can be enabled as a set through Deployment Safeguards. Azure Policy add-on is required in your AKS cluster to use them.

- [AKS Model Context Protocol (MCP) server (Public Preview)](https://azure.microsoft.com/en-us/updates?id=499326) : Model Context Protocol (MCP) server for AKS is now available as an [open source release](https://github.com/Azure/aks-mcp). This foundational component enables AI agents to interact with AKS clusters and simplifies cluster management. Get building your AKS cluster AI management tools :-)

- [Agentic experience for AKS in the Azure CLI (Private Preview)](https://azure.microsoft.com/en-us/updates?id=499377) : Second AKS AI angle of the post :-) The Azure Kubernetes Service (AKS) team is introducing a new agentic AI-powered CLI experience through the “az aks agent” command. This feature brings the intelligence of agentic reasoning directly into the Azure CLI, enabling developers and operators to interact with their clusters using natural language powered by agentic AI. Limited preview with signup - not much more information about it just now.


## Azure Storage

- [Azure Storage Discovery (Public Preview)](https://azure.microsoft.com/en-us/updates?id=499143) : [Azure Storage Discovery](https://learn.microsoft.com/en-gb/azure/storage-discovery/overview) is a fully managed service that provides enterprise-wide visibility into your Azure Blob Storage data estate. In a single pane of glass you can understand and analyze how your data estate evolved over time, optimize costs, enhance security, and drive operational efficiency. Azure Storage Discovery integrates with Copilot in Azure, enabling you to unlock insights and accelerate decision-making without utilizing any query language. Interesting service - another edition to the 'enterprise management' Azure services like API Center, and potentially very useful for getting to grips with a large Azure storage estate (Blobs, anyway, since that's the only storage service supported at this stage). [Free and Standard tiers](https://learn.microsoft.com/en-gb/azure/storage-discovery/pricing) are available.

## Network Security Perimeter

- [Network Security Perimeter (GA)](https://azure.microsoft.com/en-us/updates?id=496002) : [Network security perimeter](https://learn.microsoft.com/en-us/azure/private-link/network-security-perimeter-concepts) allows organizations to define a logical network isolation boundary for PaaS resources (for example, Azure Storage account and SQL Database server) that are deployed outside your organization’s virtual networks. It restricts public network access to PaaS resources within the perimeter; access can be exempted by using explicit access rules for public inbound and outbound. Announced in preview in December 2024. Now part of the networking config for supported resource at configuration time if you go through the wizard in the portal (e.g. Storage Accounts) - looks like Microsoft are positioning it as the 'next iteration' of Private Link and as the 'most secure' option for PaaS service networking (since the perimeter controls both inbound and outbound access to the service in question).

## Virtual Network Manager

- [Azure Virtual Network Manager mesh connectivity (Public Preview)](https://azure.microsoft.com/en-us/updates?id=499782) : [Azure Virtual Network Manager](https://learn.microsoft.com/en-us/azure/virtual-network-manager/overview) mesh connectivity is now in public preview, enabling you to group up to 5,000 virtual networks in supported regions.


