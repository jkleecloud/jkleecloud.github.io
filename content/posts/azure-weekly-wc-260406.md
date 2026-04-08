+++
title = 'Azure Snippets w/c 06/04/2026'
date = 2026-04-09T08:00:16+01:00
draft = true
categories = ['Azure Weekly 2026']
tags = ['DB for PostgreSQL', 'Redis', 'IaC', 'NSG', 'Application Gateway', 'Azure Backup', 'Virtual Network Manager', 'Compute', 'FinOps', 'Azure Storage']
+++

Summary of Azure snippets for the week commencing 6th April 2026, grouped by Azure service.

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

## Azure Kubernetes Services

- [Pod CIDR expansion in AKS (GA)](https://azure.microsoft.com/en-us/updates?id=557907) : When clusters exhaust available pod IP addresses, teams have historically been forced to rebuild environments to restore capacity, creating operational disruption. [Pod CIDR expansion](https://learn.microsoft.com/en-us/azure/aks/azure-cni-overlay-pod-expand) allows overlay‑based (e.g. CNI Overlay) AKS clusters to increase their pod IP range in place without cluster recreation. Very useful for large clusters, and can be used in conjunction with a move from e.g. kubenet to CNI Overlay networking.

- [Blue-green agent pool upgrade (Public Preview)](https://azure.microsoft.com/en-us/updates?id=557862) : In‑place node pool upgrades can introduce risk by applying changes directly to running environments. [Blue‑green agent pool upgrades](https://learn.microsoft.com/en-us/azure/aks/blue-green-node-pool-upgrade) create a parallel node pool with the new configuration, allowing validation before workloads are shifted and providing a clear rollback path. This reduces upgrade risk and supports more controlled cluster lifecycle management. Another new feature improving the experience and resilience for upgrading node pools, following last month's [node pool version rollback](https://jkleecloud.github.io/posts/azure-weekly-wc-260309/#azure-kubernetes-services) preview release.

## Azure Storage

- [User delegation SAS for Azure Tables, Azure Files, and Azure Queues (GA)](https://azure.microsoft.com/en-us/updates?id=559535) : Following [February's preview release](https://jkleecloud.github.io/posts/azure-weekly-wc-260202/#azure-storage), user delegation SAS for Azure Tables, Azure Files, and Azure Queues is now generally available. User delegation SAS allows users to [create a more secure SAS token](https://learn.microsoft.com/en-us/rest/api/storageservices/create-user-delegation-sas) than account or service SAS by tying the SAS token to the delegator. This extension of UDK SAS will allow users to set SAS tokens at the table, table entity, queue, queue entity, file container, and individual file level.



