+++
title = 'Azure Snippets w/c 20/05/2024'
date = 2024-05-24T10:56:36+01:00
draft = false
categories = ['Azure Weekly 2024']
tags = ['APIM', 'Availability Zones', 'Azure Backup', 'Redis', 'Compute', 'Azure Container Storage', 'AKS', 'ARM', 'Azure SQL', 'Log Analytics']
+++

Summary of Azure snippets for the week commencing 20th May 2024, grouped by Azure service.

GA = Generally Available  
Public/Private Preview = as stated :-)

[Microsoft Build](https://build.microsoft.com/en-US/home) took place this week, so lots of announcements - unsurprisingly, [a strong focus on Copilot and AI](https://blogs.microsoft.com/blog/2024/05/21/whats-next-microsoft-build-continues-the-evolution-and-expansion-of-ai-tools-for-developers/), though there were some other technologies covered as well. Have a look at the [Build 2024 Book of News](https://news.microsoft.com/build-2024-book-of-news/) for all the new stuff announced.

Azure services with highlighted updates this week:

- [API Management](#api-management)
- [Availability Zones](#availability-zones)
- [Azure Backup](#azure-backup)
- [Azure Cache for Redis](#azure-cache-for-redis)
- [Azure Compute](#azure-compute)
- [Azure Container Storage](#azure-container-storage)
- [Azure Kubernetes Services](#azure-kubernetes-services)
- [Azure Resource Manager](#azure-resource-manager)
- [Azure SQL](#azure-sql)
- [Log Analytics](#log-analytics)

## API Management

- OpenAI features in APIM (GA) : [Token Limit Policy](https://azure.microsoft.com/en-gb/updates/ga-azure-openai-token-limit-policy-in-azure-api-management/), [Import OpenAI endpoints](https://azure.microsoft.com/en-gb/updates/ga-import-azure-openai-enpoints-as-an-apis-in-azure-api-management/), [Emit Token Metric policy](https://azure.microsoft.com/en-gb/updates/ga-azure-openai-emit-token-metric-policy-in-azure-api-management/)
- [Backend Load Balancer (GA)](https://azure.microsoft.com/en-gb/updates/ga-load-balancer-in-azure-api-management/) : [Create a pool of API backends](https://learn.microsoft.com/en-us/azure/api-management/backends?tabs=bicep#load-balanced-pool) and load-balance them using one of the supported algorithms
- [Backend Circuit Breaker (GA)](https://azure.microsoft.com/en-gb/updates/ga-circuit-breaker-in-azure-api-management/) : Enhance API resilience and [prevent a backend being overwhelmed](https://learn.microsoft.com/en-us/azure/api-management/backends?tabs=bicep#circuit-breaker) by excessive requests

## Availability Zones

- [Inter-zone data transfer will no longer be charged for](https://azure.microsoft.com/en-gb/updates/update-on-interavailability-zone-data-transfer-pricing/) : Until recently MS charged £0.009/GB for data transfer between Availability Zones. For me, they're now the primary platform DR feature in Azure (where supported), so data transfer being made free (even from a very small cost base) is definitely helpful.

## Azure Backup

- [Migrate VMs from standard to enhanced backup policy (Public Preview)](https://azure.microsoft.com/en-gb/updates/migrate-vm-backup-std-enhanced-policy/) : Enhanced policy offers several upgrades over standard (you can back up a VM multiple times a day, for instance) and supports Premium SSD v2/Ultra disks and Trusted Launch VMs. Once migrated to Enhanced, you can't go back to standard.

## Azure Cache for Redis

- [Enterprise 1GB E1 SKU (Public Preview)](https://azure.microsoft.com/en-gb/updates/public-preview-azure-cache-for-redis-enterprise-now-offers-a-1gb-e1-sku/) : Pitched for Gen AI (surprise :-) but another more cost-effective option to explore for Redis. Available 1 June 2024.
- [Support for Entra ID authentication and authorisation (GA)](https://azure.microsoft.com/en-gb/updates/general-availability-azure-cache-for-redis-now-supports-microsoft-entra-id-authentication-and-authorization/) : Connect to your cache instance [using an Entra ID token (instead of an access key) to authenticate](https://learn.microsoft.com/en-gb/azure/azure-cache-for-redis/cache-azure-active-directory-for-authentication), and use role-based access control (via ACLs). Available for Azure Cache for Redis Basic, Standard, and Premium SKUs.

## Azure Compute

- [Azure Compute Fleet (Public Preview)](https://azure.microsoft.com/en-gb/updates/azure-fleet-preview/) : Provision and manage VMs at scale. Optimise performance and pricing within a fleet. Like AKS Fleet Manager for groups of VMs instead of AKS clusters? - seems the same sort of idea at first glance.
    - [Blog post](https://techcommunity.microsoft.com/t5/azure-compute-blog/announcing-the-public-preview-of-azure-compute-fleet/ba-p/4143031)
    - [Documentation](https://learn.microsoft.com/en-us/azure/azure-compute-fleet/overview)

## Azure Container Storage

- [Azure Container Storage (GA)](https://news.microsoft.com/build-2024-book-of-news/#a-132-azure-migrate-and-azure-container-storage-updates) : In the next month.
- [Azure Files updates for ACS (Preview)](https://news.microsoft.com/build-2024-book-of-news/#a-132-azure-migrate-and-azure-container-storage-updates) : Vaulted backups, soft delete for NFS file shares, geo-redundancy for large file shares, metadata caching.

## Azure Kubernetes Services

- [Kubernetes 1.30 support (Public Preview)](https://azure.microsoft.com/en-gb/updates/public-preview-kubernetes-version-130-support-in-aks/)
- [KEDA in the Azure Portal (GA?)](https://azure.microsoft.com/en-gb/updates/public-preview-keda-scaling-in-the-azure-portal/) : Kubernetes Event-Drive Autoscaler (KEDA) is an open-source, lightweight component that allows users to autoscale container workloads on events in external scalers. KEDA extends the functionality of the native Kubernetes Horizontal Pod Autoscaler (HPA) with a wide variety of scalers and scale-to-zero capabilities, thus allowing user applications to meet demand in a more sustainable and cost-efficient manner. (Interesting that the article says it's GA, but the URL has 'public preview' in it. This doesn't seem to be in the [KEDA docs](https://learn.microsoft.com/en-us/azure/aks/keda-about) yet either (only mentions ARM template and CLI) - approach with caution perhaps :-)
- [AKS Automatic (Public Preview)](https://azure.microsoft.com/en-gb/updates/public-preview-aks-automatic/) : Azure-managed cluster configuration and operations, including nodes, scaling, security, and other preconfigured settings. Bringing some of the management features of e.g. Container Apps to AKS clusters?
    - [Feature comparison with standard AKS](https://learn.microsoft.com/en-gb/azure/aks/intro-aks-automatic#aks-automatic-and-standard-feature-comparison).
- [Automated deployments for AKS (GA)](https://azure.microsoft.com/en-gb/updates/generally-available-automated-deployments-for-aks/) : Simplify the process of setting up a GitHub Action and creating an automated pipeline for your code releases to your AKS cluster. [Private clusters currently not supported](https://learn.microsoft.com/en-gb/azure/aks/automated-deployments).
- [In context observability for AKS object overviews in Azure Portal (GA)](https://azure.microsoft.com/en-gb/updates/azure-portal-now-offers-in-context-observability-for-aks-object-overviews/) : View CPU and memory utilisation at a namespace and workload level. More AKS observability in the portal directly - useful for seeing at a glance where there might be issues. Powered by Azure Monitor service for managed Prometheus.
- [Draft](https://github.com/Azure/draft) : Draft is an open-source MS tool that makes it easier for developers to get started building apps that run on Kubernetes by taking a non-containerized application and generating the Dockerfiles, Kubernetes manifests, Helm charts, Kustomize configuration, and other artifacts associated with a containerized application. Draft can also generate a GitHub Actions workflow file to quickly build and deploy applications onto any Kubernetes cluster. Latest update can now [validate manifests against best practices](https://azure.microsoft.com/en-gb/updates/draft-now-supports-best-practices-via-deployment-safeguards/) using [AKS deployment safeguards](https://learn.microsoft.com/en-gb/azure/aks/deployment-safeguards).
- [App Configuration Extension for AKS (Public Preview)](https://azure.microsoft.com/en-gb/updates/appconfig-aksextension/) : Allows you to install and manage the Azure App Configuration Kubernetes Provider on your AKS cluster via Azure Resource Manager (ARM).

## Azure Resource Manager

- [Azure CLI and Powershell updates from Build](https://techcommunity.microsoft.com/t5/azure-tools-blog/azure-cli-and-powershell-tools-build-2024-announcement/ba-p/4148584) : New login experience and security improvements, wider resource coverage

## Azure SQL

- [Licence-free standby replica (GA)](https://techcommunity.microsoft.com/t5/azure-sql-blog/general-availability-of-license-free-standby-replica-for-azure/ba-p/4139089) : Designate your secondary DB as a standby replica and save about 40% on costs. One DB can be designated in the General Purpose & Business Critical service tier and provisioned compute tier.

## Log Analytics

- [Cross-region workspace replication (Public Preview)](https://azure.microsoft.com/en-gb/updates/log-analytics-workspace-replication-public-preview/) : Enhance resilience for Log Analytics by replicating workspace data to a secondary region. User-initiated failover (or switchover as MS call it), transparent to apps (DNS-based). Supported in UK West and UK South.
    - [Documentation](https://learn.microsoft.com/en-gb/azure/azure-monitor/logs/workspace-replication)

