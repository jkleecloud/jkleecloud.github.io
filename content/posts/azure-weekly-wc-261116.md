+++
title = 'Azure Snippets w/c 16/11/2026'
date = 2026-11-17T08:00:16Z
draft = true
categories = ['Azure Weekly 2026']
tags = ['DB for PostgreSQL', 'AI', 'Foundry', 'Azure Backup', 'AKS', 'Azure Monitor', 'Azure SQL', 'Front Door', 'Virtual Networks']
+++

Summary of Azure snippets for the week commencing 11th November 2026, grouped by Azure service. This is a bit of a 'pre-Ignite' post - with that event happening 17th-20th November, I'm fairly sure there'll be a few announcements to cover in the next post!

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [AI/Foundry](#ai--foundry)
- [Azure Backup](#azure-backup)
- [Azure Database for PostgreSQL](#azure-database-for-postgresql)
- [Azure Kubernetes Services](#azure-kubernetes-services)
- [Azure Monitor](#azure-monitor)
- [Azure SQL](#azure-sql)
- [Front Door](#front-door)
- [Virtual Networks](#virtual-networks)

## AI / Foundry

- [Cost management and tagging for Claude models in Microsoft Foundry (GA)](https://azure.microsoft.com/en-us/updates?id=577260) : Microsoft Foundry now brings Claude models into Azure Cost Management alongside the rest of your Foundry spend. Until now, Claude charges appeared under SaaS rather than under the Foundry resource used to deploy them, and Claude deployments lacked the tags enterprises rely on for chargeback, leaving finance and platform teams to reconcile costs by hand. With this release, [Claude costs](https://learn.microsoft.com/en-gb/azure/foundry/foundry-models/concepts/claude-models-billing) appear under the associated Foundry resource.

- [Azure MCP Server 3.0 (GA)](https://azure.microsoft.com/en-gb/updates?id=578662) : [Azure MCP Server 3.0](https://devblogs.microsoft.com/azure-sdk/azure-mcp-server-3-0-stable-release/) is now generally available, expanding how AI agents and developer tools interact with Azure through the open Model Context Protocol (MCP). This release includes breaking changes. Review the upgrade guidance before updating existing integrations or shared deployments.

## Azure Backup

- [Cross Tenant Restore (Public Preview)](https://azure.microsoft.com/en-us/updates?id=577117) : [Cross-Tenant Restore (CTR)](https://learn.microsoft.com/en-gb/azure/backup/cross-tenant-restore-overview) helps organizations establish an independent recovery path by enabling Azure VM backups to be restored into a separate Azure tenant. Documentation suggests other backup types are supported as well as VMs.

## Azure Database for PostgreSQL

- [Azure Backup for PostgreSQL flexible server and elastic cluster (v2) (Public Preview)](https://azure.microsoft.com/en-us/updates?id=573425) : [Azure Backup for PostgreSQL flexible server and elastic cluster (v2)](https://learn.microsoft.com/en-us/azure/backup/backup-azure-postgresql-flex-server-elastic-cluster-v2-overview) preview brings enterprise-grade long-term retention to PostgreSQL. V2 uses physical backups based on managed disk snapshots, replacing the logical pg_dump backup approach used in v1.

- [Change from virtual network integration to a private endpoint capable network configuration (GA)](https://azure.microsoft.com/en-gb/updates?id=574541) : Now you can [change existing VNet-integrated servers](https://learn.microsoft.com/en-gb/azure/postgresql/network/how-to-migrate-vnet-private-endpoint-capable-server?tabs=portal-migrate) from delegated-subnet networking to a private endpoint-capable configuration, enabling secure access over a private IP address through Azure Private Link.

## Azure Kubernetes Services

- [Distributed accelerator for cloud storage on AKS (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=578454) : [Distributed accelerator for cloud storage (DACS)](https://learn.microsoft.com/en-us/azure/storage/container-storage/distributed-accelerator-for-cloud-storage-overview) is now in public preview for AI workloads running on Azure Kubernetes Service (AKS). DACS is a distributed read-through cache that runs within your AKS cluster and uses local NVMe disks across nodes to keep frequently read data from Azure Blob Storage close to GPU compute - it's enabled via Azure Container Storage. DACS is designed to improve performance for AI inference applications, basically.

- Application Gateway for Containers - [Private Ingress](https://azure.microsoft.com/en-gb/updates?id=576393), [MCP Gateway](https://azure.microsoft.com/en-us/updates?id=576388), [JWT Validation](https://azure.microsoft.com/en-us/updates?id=576382) (all Public Preview) : Three new previews for Application Gateway for Containers:
    - Private frontends that are reachable only through approved Azure Private Link private endpoints. [Private ingress](https://learn.microsoft.com/en-gb/azure/application-gateway/for-containers/private-ingress) supports [connectivity](https://learn.microsoft.com/en-gb/azure/application-gateway/for-containers/how-to-private-ingress-gateway-api?tabs=byo) across virtual networks, subscriptions, Microsoft Entra tenants, and Azure regions without requiring VNet peering.
    - [Model Context Protocol routing](https://learn.microsoft.com/en-gb/azure/application-gateway/for-containers/mcp-gateway) through the new MCPRoute custom resource. Platform teams can [publish MCP servers](https://learn.microsoft.com/en-gb/azure/application-gateway/for-containers/how-to-mcp-gateway-gateway-api?tabs=alb-managed) behind a stable hostname and path while centralizing TLS, JWT validation, Web Application Firewall protection, backend health monitoring, and routing policy at the gateway.
    - Centralized [JSON Web Token validation](https://learn.microsoft.com/en-us/azure/application-gateway/for-containers/jwt-validation) through the AuthPolicy custom resource. 

## Azure Monitor

- [Metrics usage insights for Azure Monitor workspace (GA)](https://azure.microsoft.com/en-us/updates?id=577165) : [Metrics usage insights](https://learn.microsoft.com/en-gb/azure/azure-monitor/metrics/metrics-usage-insights?tabs=portal) is now generally available, giving you greater visibility into what’s driving metrics usage across your Azure Monitor workspace. Monitor workspace utilization, identify unused metrics, understand usage trends, and investigate changes in ingestion volume to help optimize costs and plan capacity.

- [Advanced platform metrics for Azure Monitor (GA)](https://azure.microsoft.com/en-us/updates?id=575329) : Advanced platform metrics provide finer-grained signals that help customers more quickly and accurately identify changes and trends within their resources. With this release, customers can enable advanced platform metrics directly from the Azure portal, with an in-product banner prompting enablement for subscriptions where the feature is not yet enabled.

## Azure SQL

- [Restart databases in Azure SQL DB via the Azure portal (GA)](https://azure.microsoft.com/en-gb/updates?id=577992) : You can now [restart or fail over databases](https://learn.microsoft.com/en-us/azure/azure-sql/database/restart-database?view=azuresql) directly from the Azure portal, including single databases, Hyperscale databases, and databases in elastic pools, without writing scripts against the Rest API or contacting support.

## Front Door

- [Azure Front Door mutual TLS authentication (GA)](https://azure.microsoft.com/en-us/updates?id=577678) : [Mutual TLS (mTLS)](https://learn.microsoft.com/en-us/azure/frontdoor/mutual-tls), also known as client certificate authentication, is now generally available on Azure Front Door Premium. Use X.509 client certificates to help protect sensitive applications and APIs. General availability also simplifies trusted CA configuration. You can upload only the trusted root CA certificate to Azure Key Vault and associate it with your Front Door custom domain, without uploading intermediate CA certificates.

## Virtual Networks

- [Standard service endpoint (GA)](https://azure.microsoft.com/en-us/updates?id=571025) : [Standard service endpoint](https://learn.microsoft.com/en-us/azure/private-link/service-endpoint-standard-overview), a new capability in the Azure Private Link family, provides a scalable and secure approach for connecting Azure IaaS workloads to Azure PaaS services. Standard service endpoint addresses the manageability, and the scale limitations of traditional service endpoints by using Public IP addresses as network identifiers and integrating with network security perimeter. Standard service endpoint is a [paid Azure feature](https://azure.microsoft.com/en-us/pricing/details/private-link/) and is billed at a fixed rate per virtual network (VNet) per hour.

- [Disable VNet peering route (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=576242) : [DPR](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-peering-overview?branch=main#disable-peering-route-propagation-preview) suppresses system-generated peering routes on subnets associated with the route table while preserving the peering connection itself. In large hub-and-spoke networks, you can pair this feature with a summarized user-defined route to direct traffic through a network virtual appliance, such as Azure Firewall, instead of maintaining a separate override for every spoke. This helps simplify route management as your network grows.

- [Network Watcher VNet flow logs filtering (GA)](https://azure.microsoft.com/en-us/updates?id=577782) : [Azure Network Watcher VNet flow logs filtering](https://learn.microsoft.com/en-gb/azure/network-watcher/vnet-flow-logs-filtering) is now generally available, enabling you to control which network traffic flows are logged based on specific criteria such as IP addresses, ports, protocols, encryption state, flow state, and traffic direction. This feature is now accessible through the Azure portal, in addition to PowerShell, making it easier to configure and manage filtering for VNet flow logs directly from the portal (though the docs don't appear to have quite caught up with that change yet and are only showing PowerShell at present).