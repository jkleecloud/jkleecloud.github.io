+++
title = 'Azure Snippets w/c 12/10/2026'
date = 2026-10-13T08:00:16+01:00
draft = false
categories = ['Azure Weekly 2026']
tags = ['App Service', 'AKS', 'AI', 'Foundry', 'Virtual Networks', 'Compute', 'Azure SQL', 'Azure Storage']
+++

Summary of Azure snippets for the week commencing 12th October 2026, grouped by Azure service. A few retirements to note among the announcements this time.

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [App Service](#app-service)
- [Azure Kubernetes Services](#azure-kubernetes-services)
- [Azure SQL](#azure-sql)
- [Azure Storage](#azure-storage)
- [Compute](#compute)
- [Microsoft Foundry / AI](#microsoft-foundry--ai)
- [Virtual Networks](#virtual-networks)

## App Service

- [Support for Java 8, 11 and 17 will end on September 1, 2027 (RET)](https://azure.microsoft.com/en-us/updates?id=568585) : On September 1, 2027, [support for Java 8, 11 and 17](https://learn.microsoft.com/en-gb/azure/app-service/language-support-policy?tabs=windows#java-specific-runtime-support) will end. Apps that are hosted on App Service will continue to run, but security updates will no longer be available, and customer service will no longer be provided for Java 8, 11 and 17. Affects Functions as well as App Service-hosted apps more generally.

## Azure Kubernetes Services

- [Flex Nodes for AKS (Public Preview)](https://azure.microsoft.com/en-us/updates?id=571919) : [Flex Nodes for AKS](https://learn.microsoft.com/en-gb/azure/aks/flex-nodes-for-aks-overview) is a deployment option for application and platform teams to use hybrid and edge infrastructure as connected worker nodes to an AKS control plane in Azure. They extend Azure Kubernetes Service (AKS) to user-managed virtual machines and bare metal hosts. Use flex nodes to add existing compute capacity to an AKS cluster without moving that compute into a standard AKS node pool. This capability is useful when you need to access capacity outside the AKS cluster's Azure region.

## Azure SQL

- [Azure SQL Dev Hub (Public Preview)](https://azure.microsoft.com/en-us/updates?id=572998) : [Azure SQL Dev Hub](https://microsoft.github.io/azure-sql-dev-hub/) gives you a central starting point for building applications with Azure SQL, whether you’re developing directly or using AI agents. You can find guidance for connecting to Azure SQL from .NET, Python, Node.js, and Java, along with resources for working with schemas and queries. Significant focus on AI apps, unsurprisingly :-)

- [Zone redundancy for Azure SQL Managed Instance Next-gen General Purpose (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=568344) : The [Next-gen General Purpose service tier](https://learn.microsoft.com/en-gb/azure/azure-sql/managed-instance/service-tiers-next-gen-general-purpose-use?view=azuresql&tabs=portal) is an architectural upgrade to the existing General Purpose service tier that you can use for new and existing instances. You can now benefit from enhanced resilience with the public preview of zone redundancy for Azure SQL Managed Instance Next-gen General Purpose.

## Azure Storage

- [Agentless migration of on-premises SMB file shares to Azure Files (SMB) (Public Preview)](https://azure.microsoft.com/en-us/updates?id=570910) : Azure Storage Mover now supports [agentless migration](https://learn.microsoft.com/en-us/azure/storage-mover/agentless-on-premises-files-migration?tabs=portal) of on-premises SMB file shares to Azure Files (SMB), in public preview. You can move file data from Windows Server or NAS shares into Azure without deploying, registering, or maintaining a migration agent on-premises.

- [User-bound user delegation SAS for Azure Storage (GA)](https://azure.microsoft.com/en-us/updates?id=569241) : [Enhanced secure authentication in Azure Storage](https://techcommunity.microsoft.com/blog/azurestorageblog/generally-available-restrict-usage-of-user-delegation-sas-to-an-entra-id-identit/4554967) that combines the flexibility of [user-delegation shared access signature (SAS)](https://learn.microsoft.com/en-gb/rest/api/storageservices/create-user-delegation-sas) with the user-bound access of Entra ID. User-bound user delegation SAS allows users to create a more secure SAS token than account SAS, service SAS, or normal user delegation SAS by restricting the usage of the SAS token to an end user identity. This will help enforce that the user delegated SAS can only be used by intended users.

## Compute

- [Dv3, Dsv3, Ev3, and Esv3 Azure VMs retiring (RET)](https://azure.microsoft.com/en-us/updates?id=572346) : Microsoft is announcing the retirement of the Dv3, Dsv3, Ev3, and Esv3 Azure VM series in public cloud Azure regions. These VMs will enter the [End-of-Life lifecycle stage](https://learn.microsoft.com/en-us/azure/virtual-machines/sizes/lifecycle/lifecycle-overview) and retire on November 15, 2029. [Migration to the equivalent v5 series](https://learn.microsoft.com/en-us/azure/virtual-machines/sizes/lifecycle/sizes-v5-modernization-overview) is the simplest path forward; [migrating to v6 or v7](https://learn.microsoft.com/en-us/azure/virtual-machines/sizes/lifecycle/sizes-v6-v7-modernization-overview) requires upgrading the VM generation to Gen 2 and enabling Trusted Launch, which is more involved.

- [Microsoft Dev Box will be retired on September 18, 2028 (RET)](https://azure.microsoft.com/en-us/updates?id=567933) : RIP Dev Box - close-down began on 14th September 2026, it's no longer being developed as a service, and will be retiring in September 2028. Windows 365 is the way forward for virtualised Dev environments.

- [Azure Deployment Environments will be retired on February 22, 2027 (RET)](https://azure.microsoft.com/en-us/updates?id=567934) : Probably connected to the retirement of Dev Box, Azure Deployment Environments began closing down on 14th September 2026 and will be retired on 22nd Feb 2027. Not so clear what the recommended migration path is - a service or services will be needed to cover environment provisioning and developer self-service.

## Microsoft Foundry / AI

- [Azure Copilot Troubleshooting Agent (GA)](https://azure.microsoft.com/en-us/updates?id=570980) : [Troubleshooting Agent](https://techcommunity.microsoft.com/blog/appsonazureblog/azure-copilot-announces-general-availability-of-the-troubleshooting-agent/4554549) is a unified, built-in Azure Copilot capability that helps customers investigate and resolve operational issues faster. Available through both Azure Copilot and Support + Troubleshooting in the Azure portal.

- [Foundry Routines in Foundry Agent Service (Public Preview)](https://azure.microsoft.com/en-us/updates?id=563536) : [Foundry Routines](https://learn.microsoft.com/en-gb/azure/foundry/agents/how-to/use-routines?pivots=foundry-portal) are a native trigger primitive for running published agents automatically. Routines includes recurring schedules, one-shot delayed timers, and event-based triggers through supported connections, keeping triggers, execution, and observability inside the governed Foundry workspace. This moves the trigger layer inside Foundry and its management scope - previously it had to be built outside with e.g. Function or Logic Apps.

- [Microsoft SQL Agent Skills (Public Preview)](https://azure.microsoft.com/en-us/updates?id=573003) : [Microsoft SQL Agent Skills](https://github.com/microsoft/microsoft-sql) help you get more accurate, product-specific guidance when using AI agents to build, operate, and migrate SQL workloads. You can use these skills with Azure SQL Database, Azure SQL Database container, SQL Server to Azure migration, and Fabric Database Hub scenarios.

- [SQL Migration Agent Skills for assessment, migration, and validation (GA)](https://azure.microsoft.com/en-gb/updates?id=571899) : Part of the same repo as the SQL Agent Skills above, SQL Migration Agent Skills help you automate and streamline the end-to-end migration journey from SQL Server to Azure.

- [Azure canvases for GitHub Copilot (GA)](https://azure.microsoft.com/en-gb/updates?id=573385) : [Azure canvases for GitHub Copilot](https://developer.microsoft.com/blog/azure-canvases/) are interactive shared workspaces that bring Azure tools, dashboards, and guided workflows directly alongside your Copilot conversations. Instead of managing results entirely in chat, you can browse resources, explore cost data, and guide a workflow in a purpose-built interface while Copilot remains available to help.

- [Microsoft Agent 365 integration with Azure API Management (Public Preview)](https://azure.microsoft.com/en-us/updates?id=574204) : The integration between Microsoft Agent 365 and Azure API Management is now available in public preview, helping organizations connect centralized governance with runtime enforcement for MCP servers and tools.

## Virtual Networks

- [High-scale mesh in Azure Virtual Network Manager (GA)](https://azure.microsoft.com/en-us/updates?id=571572) : [High-scale mesh using connected groups](https://learn.microsoft.com/en-us/azure/virtual-network-manager/concept-connectivity-configuration#enable-high-scale-connectivity-in-azure-virtual-network-manager-connected-groups) in Azure Virtual Network Manager is now generally available. In available regions, customers may connect up to 3,000 virtual networks in a single mesh connectivity configuration by default and higher scale IP connectivity within those virtual networks available by request.

- [Azure Virtual Network routing appliance (GA)](https://azure.microsoft.com/en-us/updates?id=568605) : Bit late with this one, but the [Azure Virtual Network routing appliance](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-routing-appliance-overview) is now generally available. It delivers private connectivity across virtual networks, using specialized hardware for low latency, high throughput, and better performance than virtual machines.