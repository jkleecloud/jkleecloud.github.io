+++
title = 'Azure Snippets w/c 29/06/2026'
date = 2026-06-29T17:00:16+01:00
draft = false
categories = ['Azure Weekly 2026']
tags = ['AI', 'API Center', 'APIM', 'Azure Backup', 'Azure Functions', 'AKS', 'Azure Monitor', 'Azure SQL', 'Azure Storage', 'Logic Apps', 'Virtual Network Manager']
+++

Summary of Azure snippets for the week commencing 26th June 2026, grouped by Azure service.

Microsoft Build took place at the beginning of June. No Book of News this year, but all the announcements are gathered in the [News section of the Build site](https://news.microsoft.com/build-2026/#more-news). Mostly AI-related and connected to Microsoft's Frontier initiative, which probably won't come as a surprise :-) Quite a few GA announcements of other services and features as well since the last post - so this one is a bit of a bumper edition!

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [AI](#ai)
- [API Center](#api-center)
- [API Management](#api-management)
- [Azure Backup](#azure-backup)
- [Azure Functions](#azure-functions)
- [Azure Kubernetes Services](#azure-kubernetes-services)
- [Azure Monitor](#azure-monitor)
- [Azure SQL](#azure-sql)
- [Azure Storage](#azure-storage)
- [Logic Apps](#logic-apps)
- [Virtual Network Manager](#virtual-network-manager)

## AI

- [Microsoft Discovery (GA)](https://azure.microsoft.com/en-us/updates?id=562733) : [Microsoft Discovery](https://azure.microsoft.com/en-us/solutions/discovery) is now generally available, providing research and development organizations an enterprise platform for building and governing agentic AI workflows across scientific and engineering disciplines.

## API Center

- [Azure API Center now supports agent registration, agent assessment, and Git-based synchronization (GA)](https://azure.microsoft.com/en-gb/updates?id=562909) : Agents are becoming foundational enterprise assets capable of planning, reasoning, and executing multi-step tasks on behalf of applications and developers. By bringing them into a [governed catalog](https://learn.microsoft.com/en-us/azure/api-center/register-manage-agents), Azure API Center helps teams reduce duplication, improve reuse, and accelerate AI application development.

- [Azure API Center now provides a data plane MCP server for enterprise-wide discovery of APIs and AI assets (GA)](https://azure.microsoft.com/en-gb/updates?id=562914) : With this update, Azure API Center introduces a [data plane MCP server](https://learn.microsoft.com/en-us/azure/api-center/discover-catalog-mcp-server) that acts as a unified enterprise discovery endpoint — enabling agents and developer tools to access the full catalog of registered MCP servers, tools, APIs, and AI assets through a single connection.

## API Management

- [Azure API Management workspaces now support the built-in gateway (GA)](https://azure.microsoft.com/en-gb/updates?id=562848) : Organisations using [workspace-based API management](https://learn.microsoft.com/en-gb/azure/api-management/workspaces-overview) models previously needed a dedicated workspace gateway and Premium tier deployment to take advantage of API Management workspaces increasing both cost and operational complexity. With this update, Azure API Management customers can now associate workspaces directly with the built-in gateway, extending workspace support across additional tiers and all regions supported by API Management. Workspaces can be used in any tier except Consumption; the feature is currently rolling out to v2 tiers of API Management and will start rolling out to classic tiers around July or August.

- [API Management Premium v2 now supports multiple custom domains (GA)](https://azure.microsoft.com/en-gb/updates?id=562899) : With this update, Azure API Management Premium v2 enables multiple custom domains within a single instance across gateway, developer portal, and management endpoints. Previously, achieving this level of separation frequently required additional API Management instances, increasing operational complexity and cost.  

## Azure Backup

- [Snapshot backup for SQL Server in Azure VMs (Public Preview)](https://azure.microsoft.com/en-us/updates?id=564668) : Azure Backup now supports [snapshot-based backup for SQL Server running on Azure Virtual Machines](https://learn.microsoft.com/en-us/azure/backup/backup-azure-sql-database#snapshot-backup-for-sql-instances-in-azure-vm-preview). This new capability uses Azure disk snapshots combined with native SQL transaction log backups to deliver near-instant, low-impact full backups for large SQL databases, significantly improving backup performance and reducing the load on production workloads compared to streaming backups. I've been evaluting Azure Backup for SQL on VMs streaming backup recently, so this is an interesting development.

## Azure Functions

- [Azure Functions now supports hosting MCP Apps (GA)](https://azure.microsoft.com/en-gb/updates?id=562099) : Azure Functions now supports [building and hosting MCP Apps](https://learn.microsoft.com/en-gb/azure/azure-functions/scenario-mcp-apps?tabs=bash%2Clinux&pivots=programming-language-python) using the Azure Functions MCP Extension. This capability is available for Python, TypeScript, .NET, and Java.

-  [Built-in Grafana dashboards for Azure Functions (GA)](https://azure.microsoft.com/en-gb/updates?id=562492) : Azure Functions now provides [built-in Grafana dashboards](https://learn.microsoft.com/en-gb/azure/azure-functions/monitor-functions?tabs=flex-consumption-plan%2Cportal#view-built-in-grafana-dashboards). Customers now get a zero-setup, single pane of glass for the health, performance, and scale of their function apps directly in the Azure portal: no Grafana instance to provision, no data sources to wire up, and no extra cost.

- [Rolling updates in Flex Consumption (GA)](https://azure.microsoft.com/en-us/updates?id=562365) : Rolling updates are now generally available in the Flex Consumption plan for Azure Functions, delivering zero-downtime deployments with a simple configuration change. The [Rolling update strategy](https://learn.microsoft.com/en-gb/azure/azure-functions/flex-consumption-site-updates?tabs=azure-cli) provides zero-downtime deployments by draining and replacing instances in batches. In-progress executions complete naturally without forced termination. (Currently GA in limited regions in Asia and the US - rollout to other regions is in progress.)

## Azure Kubernetes Services

- [AKS Release 2026-06-19 now available (GA)](https://github.com/Azure/AKS/releases/tag/2026-06-19) : Main highlights of this release are Kubernetes v1.36 being added as a Long Term Support version, and the retirement of Windows Server 2022 nodes extended to 30th June 2028.

- [Application Gateway for Containers - Inference Gateway (Public Preview)](https://azure.microsoft.com/en-us/updates?id=566516) : The new [inference gateway capability](https://learn.microsoft.com/en-gb/azure/application-gateway/for-containers/inference-gateway) brings the Kubernetes Gateway API Inference Extension to Application Gateway for Containers, enabling load and model-aware routing for self-hosted generative AI workloads on AKS.

- [Azure Container Linux (ACL) on Azure Kubernetes Service (AKS) (GA)](https://azure.microsoft.com/en-us/updates?id=564537) : [Azure Container Linux](https://learn.microsoft.com/en-gb/azure/azure-linux/azure-container-linux-overview) is a container-optimized, immutable operating system for AKS node pools — derived from Flatcar Container Linux (presumably this is why Flatcar isn't supported on AKS any more) and built on Azure Linux RPM packages. It delivers a [locked-down, minimal host](https://techcommunity.microsoft.com/blog/linuxandopensourceblog/introducing-azure-container-linux-acl/4523411) purpose-built for running containerized workloads at scale.

- [AKS on bare metal (Public Preview)](https://blog.aks.azure.com/2026/06/02/aks-baremetal-public-preview) : A deployment option that runs Kubernetes clusters directly on physical hardware without a hypervisor layer. Install from a USB drive (it uses features of Azure Local), and register with Azure as an AKS cluster. Seems to be intended (initially at least) for small form-factor edge devices.

## Azure Monitor

- [OpenTelemetry becomes a CNCF Graduated Project](https://www.cncf.io/announcements/2026/05/21/cloud-native-computing-foundation-announces-opentelemetrys-graduation-solidifying-status-as-the-de-facto-observability-standard/) : Not strictly Azure Monitor-related, but placed here given the observed direction of travel of that service :-) [OTel](https://opentelemetry.io/) achieving Graduated status cements its position as the key unified observability standard for cloud applications.

- [Ingest OTLP signals into Azure Monitor with the OpenTelemetry Collector (GA)](https://azure.microsoft.com/en-gb/updates?id=565090) : Preview in March, GA in June for this feature! This enables you to send telemetry data directly from OpenTelemetry-instrumented applications and platforms to Azure Monitor. Enable OTLP data ingestion in Azure Monitor using Application Insights or by manually creating the required data collection endpoints, rules and workspaces. (It’s pretty clear to me that the direction of travel for Azure Monitor is towards it becoming a fully OTLP/Prometheus/Grafana-based system, which would very much align with the current cloud-native industry standards for logging and monitoring - see also the item above!)

- [Service Level Indicators (SLI) (GA)](https://azure.microsoft.com/en-us/updates?id=565159) : Azure Monitor now includes [Service Level Indicators (SLIs)](https://learn.microsoft.com/en-us/azure/azure-monitor/fundamentals/service-level-indicators-create) and Service Level Objectives (SLOs), giving teams a clearer way to measure how customers actually experience their applications. Service level indicators (SLIs) in Azure Monitor provide measurements of reliability and performance for a [service group](https://jkleecloud.github.io/posts/azure-weekly-wc-250908/#azure-service-groups) (note that Service Groups are still in public preview).

- [Simple log alerts (GA)](https://azure.microsoft.com/en-us/updates?id=561978) : This feature is designed to provide a simplified and more intuitive experience for monitoring and alerting, enhancing your ability to detect and respond to problems in near real-time. Unlike Log Search Alerts that aggregate rows over a defined period, [Simple Log Alerts](https://learn.microsoft.com/en-us/azure/azure-monitor/alerts/alerts-create-simple-alert) evaluate each row individually.

## Azure SQL

- [SQL MCP Server (GA)](https://azure.microsoft.com/en-us/updates?id=564734) : Another rapid progression from [Public Preview](https://jkleecloud.github.io/posts/azure-weekly-wc-260406/#azure-sql) to GA, [SQL MCP Server](https://learn.microsoft.com/en-us/azure/data-api-builder/mcp/) gives customers a secure, high-performance way to build agentic solutions with controlled access to production data. Built for SQL and compatible with PostgreSQL and Azure Cosmos DB. Open source and free, it runs well in Azure, on-premises, or in any cloud.

- [Agent mode for GitHub Copilot in SQL Server Management Studio (SSMS) (Public Preview)](https://azure.microsoft.com/en-us/updates?id=562637) : You can now use Agent mode for [GitHub Copilot in SSMS](https://learn.microsoft.com/en-gb/ssms/github-copilot/overview) to work with your database: investigating performance problems, tuning queries, reviewing maintenance and configuration, identifying security concerns, troubleshooting errors, and assisting with operational workflows.

 - [Microsoft Entra server principals on Azure SQL Database (GA)](https://azure.microsoft.com/en-us/updates?id=565154) : You can now create and utilize [server principals from Microsoft Entra ID](https://learn.microsoft.com/en-gb/azure/azure-sql/database/authentication-azure-ad-logins?view=azuresql), which are logins in the virtual master database of Azure SQL Database and Azure SQL Managed Instance. This brings parity with SQL logins for your Microsoft Entra identities.

## Azure Storage

- [File share-centric management model for Azure Files (GA)](https://azure.microsoft.com/en-us/updates?id=565062) : The new [file share service management experience](https://techcommunity.microsoft.com/blog/AzureStorageBlog/simpler-scalable-file-share-management-in-azure---now-generally-available/4523035) for Azure Files is now generally available for NFS 4.1 shares on SSD storage. Powered by the Microsoft.FileShares resource provider, file shares are now top-level Azure resources that you can create, secure, scale, and bill independently, without a storage account.

## Logic Apps

- [Azure Logic Apps MCP Server (GA)](https://azure.microsoft.com/en-gb/updates?id=562868) : With the GA release of the Azure Logic Apps MCP Server, developers can now [expose existing Logic Apps workflows](https://learn.microsoft.com/en-us/azure/logic-apps/create-model-context-protocol-server-standard) as MCP-compatible tools that AI agents can directly discover and invoke — without writing custom API code.

## Virtual Network Manager

- [Cross-region IPAM pool association in Azure Virtual Network Manager (GA)](https://azure.microsoft.com/en-us/updates?id=561067) : Managing IP address space across multiple regions can be difficult to scale and prone to configuration mistakes. With [cross-region IPAM pool association](https://learn.microsoft.com/en-us/azure/virtual-network-manager/concept-ip-address-management#managing-ip-address-spaces-across-multiple-regions), you can associate a single IPAM pool with virtual networks across multiple Azure regions. This helps centralize address planning, simplify governance, and maintain consistent CIDR allocation across global environments.


