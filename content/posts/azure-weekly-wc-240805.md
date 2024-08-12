+++
title = 'Azure Snippets w/c 05/08/2024'
date = 2024-08-09T08:00:16+01:00
draft = false
categories = ['Azure Weekly 2024']
tags = ['Azure Storage', 'Extended Zones', 'AKS']
+++

Summary of Azure snippets for the week commencing 5th August 2024, grouped by Azure service.

GA = Generally Available  
Public/Private Preview = as stated :-)

Azure services with highlighted updates this week:

- [Azure Extended Zones](#azure-extended-zones)
- [Azure Kubernetes Service](#azure-kubernetes-service)
- [Azure Storage](#azure-storage)

## Azure Extended Zones

- [Azure Extended Zones (Public Preview)](https://azure.microsoft.com/en-us/updates/v2/Los-Angeles-Azure-Extended-Zones) : [Extending Azure into a small-footprint deployment](https://learn.microsoft.com/en-us/azure/extended-zones/overview) (for specific services) where latency or data residency for workloads is a primary concern. Looks like the first Extended Zone is in Los Angeles.

## Azure Kubernetes Service

- [Leveraging Azure Copilot for AKS](https://techcommunity.microsoft.com/t5/azure-infrastructure-blog/leveraging-azure-copilot-for-azure-kubernetes-services-aks/ba-p/4212457) : More and deeper integration to make cluster management simpler.
- The [latest AKS release](https://github.com/Azure/AKS/releases/tag/2024-08-05) is now rolling out : 
    - AKS patch versions 1.30.3, 1.29.7, 1.28.12, 1.27.16, are now available (so check your cluster versions for any that now fall into 'N - 3' or lower).
    - The [AKS extension for Visual Studio Code](https://learn.microsoft.com/azure/aks/aks-extension-vs-code) now supports the ability to attach an ACR to your cluster, generate Kubernetes deployment files, generate Dockerfiles, and generate GitHub Actions

## Azure Storage

- [Customer Managed Planned Failover for Azure Storage (Public Preview)](https://techcommunity.microsoft.com/t5/azure-storage-blog/public-preview-customer-managed-planned-failover-for-azure/ba-p/4211726) : Finally, the ability to failover storage endpoints while they're still healthy is coming! Definitely a boon for DR testing, moving regions if there's a problem with a different service, etc. [Very limited set of regions](https://learn.microsoft.com/en-us/azure/storage/common/storage-failover-customer-managed-planned?toc=%2Fazure%2Fstorage%2Fblobs%2Ftoc.json&bc=%2Fazure%2Fstorage%2Fblobs%2Fbreadcrumb%2Ftoc.json&tabs=grs-ra-grs) supported at the moment.