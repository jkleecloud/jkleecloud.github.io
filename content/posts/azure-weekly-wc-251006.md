+++
title = 'Azure Snippets w/c 06/10/2025'
date = 2025-10-08T08:00:16+01:00
draft = false
categories = ['Azure Weekly 2025']
tags = ['Application Gateway', 'Azure Container Storage', 'AKS', 'Azure Storage', 'IaC', 'Redis', 'Virtual Networks']
+++

Summary of Azure snippets for the week commencing 6th October 2025, grouped by Azure service. Smaller update this time around, but some significant retirements to check (especially if you use Cache for Redis), along with some exciting new features for Terraform IaC on Azure.

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [Application Gateway](#application-gateway)
- [Azure Container Storage](#azure-container-storage)
- [Azure Kubernetes Services](#azure-kubernetes-services)
- [Azure Storage](#azure-storage)
- [Infrastructure as Code](#infrastructure-as-code)
- [Redis](#redis)
- [Virtual Networks](#virtual-networks)

## Application Gateway

- [Backend TLS validation controls (GA)](https://azure.microsoft.com/en-us/updates?id=503393) : Application Gateway now supports the following configurable options, giving customers greater flexibility in managing [backend TLS behaviour](https://learn.microsoft.com/en-us/azure/application-gateway/configuration-http-settings?tabs=backendhttpsettings#backend-https-validation-settings) across diverse environments: Enable or disable Certificate chain and expiry verification; Enable or disable SNI verification. With these new settings, customers can customize TLS validations to align with their infrastructure needs.

- [Dedicated connections to backends (GA)](https://azure.microsoft.com/en-us/updates?id=503398) : By default, Application Gateway reuses the idle backend connections to optimize the resource usage of TCP connections helping both the gateway and the backend servers. With the [dedicated connection setting](https://learn.microsoft.com/en-us/azure/application-gateway/configuration-http-settings?tabs=backendhttpsettings#dedicated-backend-connection), each incoming client connection is mapped to a distinct backend connection, ensuring one-to-one communication between the frontend and the backend.

- [Using Server-sent events with Application Gateway (GA)](https://azure.microsoft.com/en-us/updates?id=503909) : Azure Application Gateway supports use of Server-sent events in general availability, enabling real-time data streaming from server to client. Server-sent events utilize server push technology on a persistent HTTP connection for seamless updates to the clients. [Specific config](https://learn.microsoft.com/en-gb/azure/application-gateway/use-server-sent-events) required for both the AG and apps using this - check out the docs for more details.

## Azure Container Storage

- [Azure Container Storage v2.0.0 (GA)](https://azure.microsoft.com/en-us/updates?id=502853) : [This release](https://blog.aks.azure.com/2025/09/15/acstor-v2-ga) delivers up to 7× higher IOPS and 4× lower latency on local NVMe compared to v1.3.1, making Container Storage v2.0.0 [the fastest storage available](https://azure.microsoft.com/en-us/blog/accelerating-ai-and-databases-with-azure-container-storage-now-7-times-faster-and-open-source/) for Azure Kubernetes Service (AKS), now with zero service fees. An [open source version](https://github.com/Azure/local-csi-driver) (CSI driver) is also available for easier installation on any Kubernetes cluster.

## Azure Kubernetes Services

- [AKS Automatic (GA)](https://azure.microsoft.com/en-us/updates?id=503235) : With [AKS Automatic](https://learn.microsoft.com/en-gb/azure/aks/intro-aks-automatic), you get production-ready clusters in minutes, preconfigured with best practices for security, reliability, and scaling. Azure handles node management, networking, upgrades, and dynamic autoscaling.

- [AKS Release 2025-09-21 now available (GA)](https://github.com/Azure/AKS/releases/tag/2025-09-21) : Fairly small release, supporting the deprecation of AKS 1.31 in November and the release of AKS Automatic, alongside the usual updates.

- [Azure Monitor dashboards with Grafana in Azure Portal for AKS (Public Preview)](https://blog.aks.azure.com/2025/09/18/azure-monitor-grafana-dashboards-portal) : Azure Kubernetes Service (AKS) now offers [native Grafana dashboards](https://learn.microsoft.com/en-gb/azure/azure-monitor/visualize/visualize-use-grafana-dashboards) within the Azure portal at no additional cost. This integration eliminates the complexity of maintaining separate visualization tools while delivering Grafana's powerful capabilities directly where you need them. Metrics from Container Insights, the Kubernetes metrics server, and any configured Azure Managed Prometheus endpoints are available out-of-the-box, providing comprehensive cluster observability.

- [AI toolchain operator add-on (KAITO) for AKS (GA)](https://azure.microsoft.com/en-us/updates?id=503263) : The [AI toolchain operator add-on (KAITO)](https://learn.microsoft.com/en-us/azure/aks/ai-toolchain-operator) is now generally available on AKS, streamlining the deployment of AI inference and fine-tuning workflows using popular open-source frameworks.

## Azure Storage

- [Azure Disk Encryption retiring (RET)](https://azure.microsoft.com/en-us/updates?id=493779) : Azure Disk Encryption will be retired on September 15, 2028. Alternate disk encryption solutions such as [Encryption At Host (recommended migration path)](https://learn.microsoft.com/en-us/azure/virtual-machines/disk-encryption-migrate?tabs=CLI%2CCLI2%2CCLI3%2CCLI4%2CCLI5%2CCLI-cleanup) and CVM OS disk encryption offer broader operating system support, improved performance, and better security.

- [General Purpose v1 (GPv1) and legacy blob storage accounts retiring (RET)](https://azure.microsoft.com/en-us/updates?id=496964) : The following account types will be retired: [General purpose v1 (GPv1) storage accounts](https://learn.microsoft.com/en-us/azure/storage/common/general-purpose-version-1-account-migration-overview) (all redundancy options); [Legacy blob storage accounts](https://learn.microsoft.com/en-us/azure/storage/common/legacy-blob-storage-account-migration-overview); Files storage accounts hosted on GPv1. Customers are encouraged to [migrate to General Purpose v2 (GPv2)](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-upgrade?tabs=azure-portal) or specialized alternatives such as BlockBlobStorage or FileStorage, depending on workload requirements.

## Infrastructure as Code

- [New Terraform on Azure features (Public Preview)](https://techcommunity.microsoft.com/blog/azuretoolsblog/accelerating-infrastructure-as-code-introducing-game-changing-terraform-features/4457341) : Seamless Code Generation to Deployment Experience (generate HCL with Copilot and natural language prompts); Unified VS Code Extension: Your Complete Terraform Toolkit (single VS Code extension, code samples, Intellisense for all MS providers, Export to reverse-engineer existing infra into HCL, Policy/Preflight validation to extend terraform plan to validate against organizational policies, compliance requirements, and Azure best practices); MS Graph Provider: Extending Terraform Beyond Infrastructure (manage resources across the Microsoft platform including Microsoft 365 configurations, Windows settings, Enterprise Mobility + Security policies, and Dynamics 365 customizations).

## Redis

- [Azure Cache for Redis SKUs retiring (RET)](https://techcommunity.microsoft.com/blog/azure-managed-redis/azure-cache-for-redis-retirement-what-to-know-and-how-to-prepare/4458721) : With [Azure Managed Redis having gone GA](https://azure.microsoft.com/en-gb/updates?id=467264) in May 2025, Microsoft is [retiring Cache for Redis](https://learn.microsoft.com/en-gb/azure/azure-cache-for-redis/cache-whats-new#october-2025). Basic, Standard and Premium will be retired in September 2028, Enterprise and Enterprise Flash in March 2027; with new instance creation blocked from 1 April 2026. Check out the [retirement FAQ](https://learn.microsoft.com/en-gb/azure/azure-cache-for-redis/retirement-faq) and start [planning for migration](https://learn.microsoft.com/en-gb/azure/redis/migrate/migrate-overview) to Managed Redis.

## Virtual Networks

- [Network Security Hub (GA)](https://azure.microsoft.com/en-us/updates?id=503617) : The Azure Firewall Manager experience has been expanded and rebranded as the [Network Security Hub](https://techcommunity.microsoft.com/blog/AzureNetworkSecurityBlog/introducing-the-new-network-security-hub-in-azure/4454588) — a centralized interface that brings together Azure Firewall, Web Application Firewall (WAF), and DDoS Protection. With this new experience, customers benefit from improved navigation, consolidated service overviews, and enhanced visibility into their security coverage. The landing page now highlights common use cases, documentation, pricing, and recommended scenarios to help users get started faster. 
 