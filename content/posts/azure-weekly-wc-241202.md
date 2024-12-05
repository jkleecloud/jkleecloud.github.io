+++
title = 'Azure Snippets w/c 02/12/2024'
date = 2024-12-05T10:50:44Z
draft = true
categories = ['Azure Weekly 2024']
tags = ['DB for PostgreSQL', 'Redis', 'IaC', 'NSG', 'Application Gateway', 'Azure Backup', 'Virtual Network Manager', 'Compute', 'FinOps', 'Azure Storage']
+++

Summary of Azure snippets for the week commencing 2nd December 2024, grouped by Azure service.

It's been a little while since I posted, and this one is a bit of a bumper one with MS Ignite having finished recently - a lot of Azure updates have dropped, along with other products'. AI is unsurprisingly a big theme once again :-) Check out the [Ignite 2024 Book of News](https://news.microsoft.com/ignite-2024-book-of-news/) for all the details.

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/en-gb/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [API Center](#api-center)
- [Azure Bastion](#azure-bastion)
- [Azure Chaos Studio](#azure-chaos-studio)
- [Azure DB for PostgreSQL](#azure-db-for-postgresql)
- [Azure Kubernetes Service](#azure-kubernetes-service)
- [Azure Local](#azure-local)
- [Dev Box](#dev-box)
- [Network Security Perimeter](#network-security-perimeter)

## API Center

- [API Center Plugin for GitHub Copilot for Azure (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=469053) : With the public preview of the API Center plugin, you can now leverage GitHub Copilot for Azure for a variety of API-related tasks, including designing and generating API specs. Seems to be part of the [API Center VS Code extension](https://marketplace.visualstudio.com/items?itemName=apidev.azure-api-center).

## Azure Bastion

- [Azure Bastion Premium SKU (GA)](https://azure.microsoft.com/en-gb/updates?id=469288) : [Azure Bastion Premium](https://learn.microsoft.com/en-us/azure/bastion/bastion-overview#sku) is a new SKU to target customers handling highly sensitive virtual machine workloads. Its mission is to offer enhanced security features that ensure customer virtual machines are connected securely and to monitor VMs for any anomalies that may arise. Looks like this is 'v1' and more Premium features will come later.

## Azure Chaos Studio

- [Support for faults for AKS clusters using managed identity authentication (GA)](https://azure.microsoft.com/en-gb/updates?id=467714) : [Azure Chaos Studio](https://learn.microsoft.com/en-us/azure/chaos-studio/)’s faults for Azure Kubernetes Service clusters [now work with managed identity authentication](https://learn.microsoft.com/en-us/azure/chaos-studio/chaos-studio-aks-authentication?tabs=azure-portal). Previously, local authentication through the Kubernetes API server was the only supported authentication method.

## Azure DB for PostgreSQL

- [On-demand backups for Azure Database for PostgreSQL - Flexible Server (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=467509) : Now you can create physical snapshots of Azure Database for PostgreSQL - Flexible Server based on your business needs. This feature complements the scheduled automated backups offered by the service, while adding the flexibility to delete the on-demand backups to help you manage costs effectively. Useful for testing, upgrades etc. when you want a very recent backup available.[Documentation](https://learn.microsoft.com/en-us/azure/postgresql/flexible-server/concepts-backup-restore#on-demand-backups-preview).

## Azure Kubernetes Service

- [Network isolated cluster in AKS (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=466980) : AKS now provides the option to use network isolated clusters to simplify the process of restricting network access and reduce the risk of unintentional exposure of the cluster's public endpoints to prevent security breaches. Outbound network traffic control for AKS without having to use Azure Firewall - see [the docs](https://learn.microsoft.com/en-gb/azure/aks/concepts-network-isolated) for more details.
- [Web Application Firewall (WAF) running on Application Gateway for Containers (Private Preview)](https://azure.microsoft.com/en-gb/updates?id=468587) : Application Gateway for Containers now supports Web Application Firewall (WAF) in private preview. Need to sign up for this one.

## Azure Local

- [Azure Local (GA)](https://azure.microsoft.com/en-gb/updates?id=467372) : This is the [next evolution of Azure Stack](https://learn.microsoft.com/en-gb/azure/azure-local/rename-to-azure-local), tying on-prem infrastructure in to the Azure cloud via Azure Arc. Lots of information available in the [Azure Arc blog post](https://techcommunity.microsoft.com/blog/azurearcblog/introducing-azure-local-cloud-infrastructure-for-distributed-locations-enabled-b/4296017) and the [Ignite book of news article](https://news.microsoft.com/ignite-2024-book-of-news/#a-331-azure-expands-adaptive-cloud-introduces-azure-local-infrastructure-solution-).

## Dev Box

- [New features (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=468062) : New features in Dev Box that make it easier to configure task-based workstations for development teams and enhance project guardrails. Includes team customisations (Dev team leads can create project-based configurations for their entire team, with the tools, packages and settings in a single config file), imaging (team customisations can be converted to images) and Project Policy (IT Admins can set up guardrails around resources that projects can and cannot access, such as images, SKUs, and network connections). Lots of details behind these - check out the [Ignite blog post](https://devblogs.microsoft.com/develop-from-the-cloud/devboxignite2024/) for more info. (There are also [new features in Deployment Environments](https://azure.microsoft.com/en-gb/updates?id=468076), which is a [complementary service to Dev Box](https://learn.microsoft.com/en-gb/azure/deployment-environments/overview-what-is-azure-deployment-environments#components-shared-with-microsoft-dev-box), for [templated project infrastructure](https://devblogs.microsoft.com/develop-from-the-cloud/adeignite2024/).)

## Network Security Perimeter

- [Network Security Perimeter (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=469298) : Network Security Perimeter allows organisations to define a logical network isolation boundary for PaaS resources (for example, Azure Storage account and SQL Database server) that are deployed outside your organisation’s virtual networks. It restricts public network access to PaaS resources within the perimeter; access can be exempted by using explicit access rules for public inbound and outbound. Looks like it builds on resources like Private Link and the ideas of NSGs and resource firewalls, to allow you to create a 'secure enclave' for PaaS resources. Interestingly, it onboards PaaS resources by 'learning' access patterns. Preview is available in all public regions, but the associated Log Analytics workspace can only be in 1 of 6 US regions at present. Check out [the documentation](https://learn.microsoft.com/en-us/azure/private-link/network-security-perimeter-concepts) for more details