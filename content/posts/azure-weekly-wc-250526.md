+++
title = 'Azure Snippets w/c 26/05/2025'
date = 2025-06-02T08:00:16+01:00
draft = false
categories = ['Azure Weekly 2025']
tags = ['API Center', 'APIM', 'AKS', 'Azure Backup', 'Azure Storage', 'Azure Monitor', 'Networking', 'Compute', 'Dev Box', 'Governance', 'IaC', 'Planetary Computer']
+++

Summary of Azure snippets for the week commencing 26th May 2025, grouped by Azure service.

With Build taking place last week, a lot of announcements have dropped as usual, so this is a fairly big post. The [Build 2025 Book of News](https://news.microsoft.com/build-2025-book-of-news/) has all the details of announcements from there. Plenty of AI focus as usual - I'll cover some of the stuff that isn't AI-related here :-)

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [API Center](#api-center)
- [API Management](#api-management)
- [Azure Backup](#azure-backup)
- [Azure Kubernetes Services](#azure-kubernetes-services)
- [Azure Monitor](#azure-monitor)
- [Azure Storage](#azure-storage)
- [Compute](#compute)
- [Dev Box](#dev-box)
- [Governance](#governance)
- [Infrastructure as Code](#infrastructure-as-code)
- [Networking](#networking)
- [Planetary Computer](#planetary-computer)

## API Center

- [New Free Tier (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=492168) : This one's probably not surprising as API Center is extremely expensive if you're not at the large enterprise scale it assumes. The [Free plan is much more limited](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/azure-subscription-service-limits?toc=%2Fazure%2Fapi-center%2Ftoc.json&bc=%2Fazure%2Fapi-center%2Fbreadcrumb%2Ftoc.json#azure-api-center-limits) than Standard, which also isn't surprising!

## API Management

- [Premium v2 Tier for Azure API Management (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=492158) : APIM v2 tiers continue to expand with a [Premium v2 tier](https://techcommunity.microsoft.com/blog/integrationsonazureblog/announcing-the-open-public-preview-of-the-premium-v2-tier-of-azure-api-managemen/4415359) joining Basic and Standard. The API Management v2 tiers (SKUs) are built on a new, more reliable and scalable platform and are designed to make API Management accessible to a broader set of customers and offer flexible options for a wider variety of scenarios. Main update for Premium v2 seems to be a new and improved VNet injection model. Currently available only in 6 regions (including UK South).

- [Model Context Protocol support in Azure API Management and Azure API Center (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=491990) : MCP is an open standard to enable connections between AI models and external tools and systems, so its introduction into APIM could be significant for developing AI-enabled APIs.

- [Applications in Azure API Management (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=492163) : Register APIs as Entra ID applications directly from APIM, and those APIs can be protected by Entra ID and use OAuth 2.0 to authenticate access. Enabled by APIM's new support for built-in OAuth 2.0 application-based access to product APIs using the client credentials flow. With [Applications](https://techcommunity.microsoft.com/blog/integrationsonazureblog/announcing-the-public-preview-of-the-applications-feature-in-azure-api-managemen/4415777), API publishers and developers can now more effectively manage client identity, access, and authorisation flows.

- [Session-aware load balancing (GA)](https://azure.microsoft.com/en-gb/updates?id=491975) : With this feature, requests from the same user session are [consistently routed to the same backend](https://learn.microsoft.com/en-us/azure/api-management/backends?tabs=portal#session-awareness), enabling support for advanced stateful scenarios such as the OpenAI Assistant API and Batch API. Seems to be introduced primarily for AI support, as it's rolling out to the AI Gateway first.

- [Inbound Private Endpoint Support for Azure API Management Standard v2 (GA)](https://azure.microsoft.com/en-gb/updates?id=492607) : This brings the Standard v2 tier in line with the 'classic' Standard tier in terms of protecting the Gateway behind a Private Endpoint.

## Azure Backup

- [GRS and CRR support for Azure VMs using Premium SSD v2 in Azure Backup available in more regions (GA)](https://azure.microsoft.com/en-gb/updates?id=494540) : Vaults used for backing up VMs with Premium SSD v2 disks in UK South and UK West (along with other new regions) can now be Geo-redundant and have Cross-Region Restore enabled.

- [Vaulted Backups by Azure Backup for Azure Database for PostgreSQL – Flexible Server in all regions (GA)](https://azure.microsoft.com/en-gb/updates?id=491576) : Azure Backup continues to expand to protect new services and standardise backup functionality on the 'operational' and 'vaulted' tier model. [Azure DB for PostgreSQL can now be backed up to a Backup Vault](https://learn.microsoft.com/en-us/azure/backup/backup-azure-database-postgresql-flex-overview) for long-term retention and higher resilience - and backups can be monitored centrally with other services in the Business Continuity Centre.

## Azure Kubernetes Services

- [AKS Release 2025-05-19 now available (GA)](https://github.com/Azure/AKS/releases/tag/2025-05-19) : Among other new features, Kubernetes 1.31 and 1.32 are now designated as LTS, and Kubernetes 1.33 is available in preview.

- [Every AKS version is now long term support (LTS) compatible (GA)](https://azure.microsoft.com/en-gb/updates?id=492579) : This is a big one for those who can't upgrade AKS on the community support release cadence - AKS will now ensure that every community version released (GA) is compatible with long term support (LTS), starting with version 1.28 LTS from April 2025. Versions 1.27, 1.28, 1.29, and 1.30 are now LTS, with 1.31 and 1.32 in the 19th May release (see above). Check out the [release calendar](https://learn.microsoft.com/en-us/azure/aks/supported-kubernetes-versions?tabs=azure-cli) in the docs to see the lifecycle timelines for each K8s version in AKS from 1.27 onwards.

- [Automated deployments in AKS now supports Azure DevOps (ADO), AKS-ready templates and service connectors (GA)](https://azure.microsoft.com/en-gb/updates?id=491875) : It's probably about time that AKS fully supported ADO as well as GitHub for [automated deployments](https://learn.microsoft.com/en-gb/azure/aks/automated-deployments?tabs=generate-dockerfile%2Cexisting-kubernetes-manifests%2Cexpose-ingress) :-) [Service connectors](https://learn.microsoft.com/en-us/azure/service-connector/quickstart-portal-aks-connection?tabs=UMI) look very useful as well - they allow for seamless connection of apps in AKS to backing resources such as Azure SQL.

- [Track AKS supported Kubernetes version regional updates in the AKS release tracker (GA)](https://azure.microsoft.com/en-gb/updates?id=491890) : AKS supported Kubernetes version release updates are now available in the [AKS release tracker](https://releases.aks.azure.com/webpage/index.html). Users can check current in-support Kubernetes versions and LTS versions for a specific region and track the release progress of new patch versions. This is a really useful update - you can see at a glance which versions are deployed in a region, which are LTS or in preview, and which have been recently deprecated.

- [Entity Tags (eTags) for Concurrency Control (GA)](https://azure.microsoft.com/en-gb/updates?id=491865) : Cluster operators and platform teams managing shared Azure Kubernetes Service (AKS) environments often face challenges with conflicting update requests—especially when multiple users or systems interact with the same resource simultaneously. This can result in unintended overwrites or inconsistent states. The [Entity Tags (eTags)](https://learn.microsoft.com/en-us/azure/aks/use-etags) feature in AKS provides a built-in mechanism to detect and prevent conflicting operations.

- [Connected registry in Azure Container Registry (ACR) (GA)](https://azure.microsoft.com/en-gb/updates?id=491948) : [Sync an Azure Container Registry](https://learn.microsoft.com/en-us/azure/container-registry/intro-connected-registry) in the cloud with a local (on-premises) registry connected to an Arc-enabled Kubernetes cluster.

- [Smart VM defaults (GA) ](https://azure.microsoft.com/en-gb/updates?id=491923): [Smart VM defaults](https://learn.microsoft.com/en-gb/azure/aks/core-aks-concepts#vm-size-and-image) automatically select the optimal default VM SKU for AKS nodes based on available capacity and quota. This feature ensures that deployments are matched with the best possible SKU, enhancing performance and reliability while optimizing resource utilization. Previously, the default AKS VM SKU was typically Standard_DS2_V2, but now you can expect dynamic outcomes in default provisioning based on SKU availability. (And, presumably, that default needs to change due to the [retirement of the D*v2 VM SKUs](https://jkleecloud.github.io/posts/azure-weekly-wc-250519/#compute).)

- [Core Kubernetes extensions for AKS (GA)](https://azure.microsoft.com/en-gb/updates?id=491895) : Core Kubernetes extensions for AKS offers an [ARM-driven experience](https://learn.microsoft.com/en-us/azure/aks/cluster-extensions) for the installation and lifecycle management of essential components that can be integrated into your AKS cluster to enhance its functionality. Currently includes extensions such as [Dapr, Flux, and Azure Backup for AKS among others](https://learn.microsoft.com/en-us/azure/aks/cluster-extensions#currently-available-extensions). Only works with clusters using managed identities, not service principals.

- [Custom certificate authority support (GA)](https://azure.microsoft.com/en-gb/updates?id=491885) : CAs allow you to [establish trust](https://learn.microsoft.com/en-gb/azure/aks/custom-certificate-authority) between your Azure Kubernetes Service (AKS) cluster and your workloads, such as private registries, proxies, and firewalls. A Kubernetes secret is used to store the certificate authority's information until it is passed to all nodes in the cluster. This could be really useful for private AKS clusters in organisations hosting their own internal CAs.

- **Enhanced integrations with Defender for Cloud (Public Preview)** : Several preview features enhancing integration between AKS and [Defender for Cloud](https://learn.microsoft.com/en-gb/azure/defender-for-cloud/defender-for-containers-introduction) with the Defender for Containers plan:
    - [Onboarding of individual AKS clusters](https://azure.microsoft.com/en-gb/updates?id=491855)
    - [AKS security dashboard](https://azure.microsoft.com/en-gb/updates?id=491850)
    - [Vulnerability assessment and malware detection for AKS nodes](https://azure.microsoft.com/en-gb/updates?id=491840)
    - [Gating vulnerable deployments in AKS](https://azure.microsoft.com/en-gb/updates?id=491825)
    - [Agentless runtime vulnerability assessment for AKS-owned images](https://azure.microsoft.com/en-gb/updates?id=491830)

## Azure Monitor

- [Granular RBAC in Azure Monitor Log Analytics (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=490961) : On top of the existing capabilities of Azure Monitor Log Analytics Workspace and table level access, you can now maintain all your data in a single Log Analytics workspace and [provide least-privilege access at any level](https://learn.microsoft.com/en-gb/azure/azure-monitor/logs/granular-rbac-log-analytics), using Azure Attribute-Based Access Control (ABAC) as part of your Azure role assignment. This capability allows you to filter the data that each user can view or query, based on the conditions that you specify. This means that you can now control which users can access which tables and rows (Row Level RBAC), based on your business or security needs and defined criteria.

## Azure Storage

- [Availability Set support for Premium SSD v2 Disk Storage (GA)](https://azure.microsoft.com/en-gb/updates?id=494088) : [Support for Availability Sets](https://learn.microsoft.com/en-us/azure/virtual-machines/use-premium-ssd-v2-with-availability-set?tabs=CLI) is now available with Premium SSD v2 (Pv2) disk storage in regions without Availability Zones - including UK West. Removes a fairly major obstacle to using Premium SSD v2 disks in regions without AZs.

- [Live Resize for Premium SSD v2 and Ultra NVMe Disks (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=495106) : This feature allows you to dynamically expand the storage capacity of your disks without any disruption to your applications. To optimize costs, you can start with smaller disks and gradually increase their storage capacity as needed, all without experiencing any downtime. [Limited regions only](https://learn.microsoft.com/en-us/azure/virtual-machines/windows/expand-disks#expand-without-downtime) at present.

## Compute

- [Network Optimized Azure Virtual Machines - Dnsv6, Dndsv6, Dnlsv6, Dnldsv6, Ensv6 and Endsv6 (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=484834) : The new [Network Optimized sizes](https://techcommunity.microsoft.com/blog/azurecompute/announcing-preview-of-new-azure-dnldnen-v6-vms-powered-by-intel-5th-gen-processo/4413459?previewMessage=true) make use of enhancements provided by Azure Boost to deliver increased network bandwidth per vCPU, a greater number of vNICs, and significantly improved connection setup performance. For those applications that really need high performance networking!

## Dev Box

- [Empower AI development with new features in Microsoft Dev Box (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=492632) : With the [new capabilities in Dev Box](https://devblogs.microsoft.com/develop-from-the-cloud/unlock-developer-potential-with-microsoft-dev-box/), developers can build AI apps effectively with quick, controlled access to serverless GPU resources, streamlined project-based configurations, and new AI-powered workflows. Includes: Serverless GPU support, preconfigured Azure AI resources, MCP server, and Authoring agent (GitHub Copilot in VS Code).

## Governance

- [Azure Quota Groups (GA)](https://azure.microsoft.com/en-gb/updates?id=495605) : This feature enables quota sharing across a group of subscriptions, reducing the number of individual quota transactions. Quota management is elevated from the subscription level to a Quota Group Azure Resource Manager (ARM) object, allowing customers to manage procured quota within a group through self-service — without Microsoft approval. This brings [quota management onto the same level as management groups](https://learn.microsoft.com/en-us/azure/quotas/quota-groups?tabs=rest-1%2Crest-2%2Crest-3%2Crest-4%2Crest-5), and allows a centrally managed quota to be shared across multiple subscriptions - unused quota can be assigned to subs that can use it without needing a support request ticket.

- [Azure SRE Agent (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=494483) : [Azure SRE agent](https://techcommunity.microsoft.com/blog/azurepaasblog/introducing-azure-sre-agent/4414569) is a new agentic AI service that can free developers from the constant stress of late-night alerts by monitoring production systems 24/7, responding to incidents in real time, and autonomously troubleshooting issues as they arise.

## Infrastructure as Code

- [GitHub Copilot for Azure (GA)](https://azure.microsoft.com/en-gb/updates?id=492584) : With features to help you create deployments with Bicep and Terraform, efficient issue identification and resolution, and deep integration with Azure resources, GitHub Copilot for Azure empowers developers to build, manage, and troubleshoot applications effortlessly.

## Networking

- [Private Subnet (GA)](https://azure.microsoft.com/en-gb/updates?id=492953) : Essentially, this removes the 'implicit' [default outbound connectivity](https://learn.microsoft.com/en-us/azure/virtual-network/ip-services/default-outbound-access) to the Internet that e.g. VMs have when created in a network without an 'explicit' outbound connection mechanism, which is through default public IP addresses that aren't very visible. With a private subnet, you'll need to explicitly create an outbound connectivity method, such as a NAT Gateway or Public IP address. Important to note that this will be the default deployment mode for all new VNets/subnets after 30th September 2025. (NAT Gateways and Public IP addresses, of course, are not free :-)

- [VM Network Troubleshooter (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=491437) : Customers can identify blocked ports faster with the Azure Portal's latest enhancement. The VM Overview blade in the Azure Portal has a new [troubleshooter tool](https://learn.microsoft.com/en-gb/azure/network-watcher/vm-network-troubleshooter) allowing users to run network diagnostics and check for common ports (HTTP/S and RDP at the moment) being blocked. Anyone who's had to troubleshoot VM connectivity will most likely appreciate anything that makes it easier!

## Planetary Computer

- [Microsoft Planetary Computer Pro (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=494165) : [Microsoft Planetary Computer Pro](https://azure.microsoft.com/en-us/products/planetary-computer-pro) is a comprehensive geospatial data platform designed to accelerate the generation of geospatial insights and their integration into enterprise Data & AI workflows.
