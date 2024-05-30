+++
title = 'Azure Snippets w/c 27/05/2024'
date = 2024-05-31T08:00:16+01:00
draft = true
categories = ['Azure Weekly 2024']
tags = ['API Center', 'AKS', 'Azure Site Recovery', 'ARM', 'Azure SQL', 'Azure SQL Managed Instance']
+++

Summary of Azure snippets for the week commencing 27th May 2024, grouped by Azure service.

GA = Generally Available  
Public/Private Preview = as stated :-)

Azure services with highlighted updates this week:

- [API Center](#api-center)
- [Azure Kubernetes Services](#azure-kubernetes-services)
- [Azure Resource Manager](#azure-resource-manager)
- [Azure Site Recovery](#azure-site-recovery)
- [Azure SQL](#azure-sql)

## API Center

- [Azure API Center Extension for VS Code (GA)](https://azure.microsoft.com/en-gb/updates/general-availability-azure-api-center-extension-for-vs-code/) : [Build, discover, try, and consume APIs](https://learn.microsoft.com/en-us/azure/api-center/use-vscode-extension) in your API center

## Azure Kubernetes Services

- [Advanced Container Networking Services for AKS (Public Preview)](https://azure.microsoft.com/en-gb/updates/advanced-container-networking-services/) : A new [suite of services bringing advanced network monitoring and diagnostics](https://learn.microsoft.com/en-gb/azure/aks/advanced-container-networking-services-overview) to AKS clusters. Currently includes only Advanced Network Observability as its inaugural and foundational feature - more are planned.
    - [Advanced Network Observability](https://learn.microsoft.com/en-gb/azure/aks/advanced-network-observability-concepts?tabs=non-cilium) is based on [Hubble](https://github.com/cilium/hubble) (itself based on Cilium, but both Cilium (with Kubernetes 1.29) and non-Cilium AKS data planes are supported). It uses Grafana and Prometheus for visualisation (Azure-managed or bring your own), and [Retina](https://retina.sh/) on non-Cilium nodes (presumably as the eBPF 'bridge'). It also supports all Azure CNI variants including kubenet.
- [Open Service Mesh deprecation](https://learn.microsoft.com/en-gb/azure/aks/open-service-mesh-about) : I noticed when looking through the AKS LTS docs that Open Service Mesh was [noted as being deprecated](https://learn.microsoft.com/en-gb/azure/aks/long-term-support#long-term-support-add-ons-and-features). Looks like the CNCF are retiring it and [Istio](https://learn.microsoft.com/en-gb/azure/aks/istio-about) is currently the only option for an AKS-supported service mesh.

## Azure Resource Manager

- [Deployment Stacks (GA)](https://techcommunity.microsoft.com/t5/azure-governance-and-management/arm-deployment-stacks-now-ga/ba-p/4145469) : [Deployment stacks](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/deployment-stacks) are an Azure resource type which provide a means of managing a collection of Azure resources as a single unit. They are designed to work primarily with [Bicep](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/overview), and are essentially a replacement for Blueprints (which never made it out of preview).

## Azure Site Recovery

- [Reporting Capabilities for Azure Site Recovery (Preview)](https://azure.microsoft.com/en-gb/updates/preview-introducing-reporting-capabilities-for-azure-site-recovery/) : Full-featured and customisable reports based on Azure Monitor logs. Available via Business Continuity Center, Recovery Services Vault and Backup Center
    - [Blog post](https://techcommunity.microsoft.com/t5/azure-governance-and-management/preview-introducing-reporting-capabilities-for-azure-site/ba-p/4148458)
    - [Documentation](https://learn.microsoft.com/en-us/azure/site-recovery/report-site-recovery)
- [Monitoring improvements for ASR](https://azure.microsoft.com/en-gb/updates/introducing-reporting-capabilities-for-azure-site-recovery/) : An improved alerting solution for Azure Site Recovery, including default alerts via Azure Monitor. Brings ASR alerting into the Azure Monitor alerts space for a more consistent experience.
    - [Blog post](https://techcommunity.microsoft.com/t5/azure-governance-and-management/monitor-effectively-using-azure-monitor-for-azure-site-recovery/ba-p/4148504)
    - [Documentation](https://learn.microsoft.com/en-us/azure/site-recovery/site-recovery-monitor-and-troubleshoot)

## Azure SQL

- [Availability portal metric (Public Preview)](https://techcommunity.microsoft.com/t5/azure-sql-blog/azure-sql-db-availability-portal-metric/ba-p/4139206) : [Monitor SLA-compliant availability](https://learn.microsoft.com/en-gb/azure/azure-sql/database/monitoring-metrics-alerts?view=azuresql#availability-metric) of Azure SQL databases in the Azure portal. Supported for DTU and vCore-based DBs at all service tiers, and for single DBs and elastic pools.
- [Update policy for Managed Instances (GA)](https://techcommunity.microsoft.com/t5/azure-sql-blog/update-policy-for-azure-sql-managed-instance/ba-p/4148968) : [Choose the speed of updates for new SQL engine features](https://learn.microsoft.com/en-us/azure/azure-sql/managed-instance/update-policy?view=azuresql&tabs=azure-portal) for your managed instance:
    - **Always up to date** (engine features deployed as soon as they are released in Azure, without waiting for the next major release of SQL Server) or **SQL Server 2022** (follows the mainstream servicing lifecycle of SQL Server 2022, with no new SQL engine features deployed until SQL Server vNext is released).
    - The former brings new functionality faster but keeps the database format changing (so e.g. restores or replication to other ('on-premises') SQL Server instances might break); latter keeps the SQL engine at 2022 (you still get Azure SQL platform updates) and maintains the database compatibility level, but no new features until SQL vNext.
    - Can change from SQL 2022 policy to Always up to date, but cannot go the other way as DB format can't be downgraded.
