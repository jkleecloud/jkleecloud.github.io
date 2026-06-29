+++
title = 'Azure Snippets w/c 29/06/2026'
date = 2026-09-09T08:00:16+01:00
draft = true
categories = ['Azure Weekly 2026']
tags = ['DB for PostgreSQL', 'Redis', 'IaC', 'NSG', 'Application Gateway', 'Azure Backup', 'Virtual Network Manager', 'Compute', 'FinOps', 'Azure Storage']
+++

Summary of Azure snippets for the week commencing 26th June 2026, grouped by Azure service.

Microsoft Build took place at the beginning of June. No Book of News this year, but all the annoucements are gathered in the [News section of the Build site](https://news.microsoft.com/build-2026/#more-news). Mostly AI-related and connected to Microsoft's Frontier initiative, which probably won't come as a surprise :-)

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [Application Gateway](#application-gateway)
- [Azure Backup](#azure-backup)
- [Azure Cache for Redis](#azure-cache-for-redis)
- [Azure DB for PostgreSQL](#azure-db-for-postgresql)
- [Azure Kubernetes Services](#azure-kubernetes-services)
- [Infrastructure as Code](#infrastructure-as-code)
- [Network Security Groups](#network-security-groups)
- [Virtual Network Manager](#virtual-network-manager)

## API Management

- [Azure API Management workspaces now support the built-in gateway (GA)](https://azure.microsoft.com/en-gb/updates?id=562848) : Organizations using [workspace-based API management](https://learn.microsoft.com/en-gb/azure/api-management/workspaces-overview) models previously needed a dedicated workspace gateway and Premium tier deployment to take advantage of API Management workspaces increasing both cost and operational complexity. With this update, Azure API Management customers can now associate workspaces directly with the built-in gateway, extending workspace support across additional tiers and all regions supported by API Management. Workspaces can be used in any tier except Consumption; the feature is currently rolling out to v2 tiers of API Management and will start rolling out to classic tiers around July or August.

## Azure Functions

- [Azure Functions now supports hosting MCP Apps (GA)](https://azure.microsoft.com/en-gb/updates?id=562099) : Azure Functions now supports [building and hosting MCP Apps](https://learn.microsoft.com/en-gb/azure/azure-functions/scenario-mcp-apps?tabs=bash%2Clinux&pivots=programming-language-python) using the Azure Functions MCP Extension. This capability is available for Python, TypeScript, .NET, and Java.

## Azure Kubernetes Services

- [AKS Release 2026-06-19 now available (GA)](https://github.com/Azure/AKS/releases/tag/2026-06-19) : Main highlights of this release are Kubernetes v1.36 being added as a Long Term Support version, and the retirement of Windows Server 2022 nodes extended to 30th June 2028.

- [Application Gateway for Containers - Inference Gateway (Public Preview)](https://azure.microsoft.com/en-us/updates?id=566516) : The new [inference gateway capability](https://learn.microsoft.com/en-gb/azure/application-gateway/for-containers/inference-gateway) brings the Kubernetes Gateway API Inference Extension to Application Gateway for Containers, enabling load and model-aware routing for self-hosted generative AI workloads on AKS.

## Azure Monitor

- [OpenTelemetry becomes a CNCF Graduated Project](https://www.cncf.io/announcements/2026/05/21/cloud-native-computing-foundation-announces-opentelemetrys-graduation-solidifying-status-as-the-de-facto-observability-standard/) : Not strictly Azure Monitor-related, but placed here given the observed direction of travel of that service :-) [OTel](https://opentelemetry.io/) achieving Graduated status cements its position as the key unified observability standard for cloud applications.

## Azure SQL

- [SQL MCP Server (GA)](https://azure.microsoft.com/en-us/updates?id=564734) : Another rapid progression from [Public Preview](https://jkleecloud.github.io/posts/azure-weekly-wc-260406/#azure-sql) to GA, [SQL MCP Server](https://learn.microsoft.com/en-us/azure/data-api-builder/mcp/) gives customers a secure, high-performance way to build agentic solutions with controlled access to production data. Built for SQL and compatible with PostgreSQL and Azure Cosmos DB. Open source and free, it runs well in Azure, on-premises, or in any cloud. 


