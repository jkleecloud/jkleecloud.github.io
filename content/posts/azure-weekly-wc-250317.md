+++
title = 'Azure Snippets w/c 17/03/2025'
date = 2025-03-21T08:00:10Z
draft = false
categories = ['Azure Weekly 2025']
tags = ['AKS', 'Azure Backup', 'Azure Load Balancer', 'Azure Storage', 'Virtual Network Manager']
+++

Summary of Azure snippets for the week commencing 17th March 2025, grouped by Azure service. Notably, the AKS updates this time include a pretty significant networking retirement.

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [Azure Backup](#azure-backup)
- [Azure Kubernetes Services](#azure-kubernetes-services)
- [Azure Load Balancer](#azure-load-balancer)
- [Azure Storage](#azure-storage)
- [Virtual Network Manager](#virtual-network-manager)

## Azure Backup

 - [Vaulted Backup for Azure Database for PostgreSQL Flexible Server (GA)](https://azure.microsoft.com/en-gb/updates?id=482997) : Generally available in 5 regions (including UK South and UK West), public preview in others. Definite enhancement to DB for PostgreSQL backups which were previously only available with the server. Good to see more services coming in to Azure Backup to take advantage of the enhanced resilience and security a Vault can provide.

 - [Vaulted Backup for Azure Files Standard shares (GA)](https://azure.microsoft.com/en-gb/updates?id=482659) : Finally, [Azure Files backups can be moved into a Vault](https://learn.microsoft.com/en-us/azure/backup/backup-azure-files?tabs=recovery-services-vault)! Enhanced data protection with the ability to configure snapshot and vaulted backup in a single policy, with cross-account/regional recovery. (Vaulted backup for Premium files is in Public Preview.)

## Azure Kubernetes Services

- [Kubenet networking for AKS to be retired in March 2028 (RET)](https://azure.microsoft.com/en-gb/updates?id=485172) : On March 31, 2028, kubenet networking for Azure Kubernetes Service (AKS) will be retired. CNI overlay networking is now the way forward if you want to do kubenet-style networking in AKS - MS have [instructions for migrating AKS clusters to CNI overlay](https://learn.microsoft.com/en-gb/azure/aks/upgrade-aks-ipam-and-dataplane). If you use kubenet networking in your AKS clusters, I'd recommend starting to plan a migration as soon as possible.

- [Azure CNI powered by Cilium Node Subnet support in AKS (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=482225) : This enhancement allows users to configure AKS clusters with Azure CNI powered by Cilium and Node Subnet. Thereby, it extends compatibility of Cilium’s eBPF dataplane to all supported IP address management configurations on AKS clusters.

- [Node Auto-Repair Kubernetes Events in AKS (GA)](https://azure.microsoft.com/en-gb/updates?id=484131) : You can now [monitor node auto-repair using the new Kubernetes events](https://learn.microsoft.com/en-us/azure/aks/node-auto-repair#monitor-node-auto-repair-using-kubernetes-events), which will notify you whenever node auto-repair initiates and finishes repair actions in your cluster. Node auto-repair is a built-in process which automatically detects unhealthy nodes and attempts to repair them through reboot, reimage, and redeploy actions.

- [Control Plane Azure Platform Metrics in AKS (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=484112) : You can now [monitor your AKS cluster control plane components](https://learn.microsoft.com/en-us/azure/aks/control-plane-metrics-monitor) such as the API server and ETCD using the new Azure platform metrics for control plane. The metrics provide insight into the availability and performance of your managed control plane components, helping you detect and resolve issues relating to the control plane. Currently only supports Azure Monitor managed Prometheus, and doesn't support Private link (so you can't monitor private clusters at present).

- [Windows Support for Virtual Machines Node Pools (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=484136) : Windows support for Virtual Machines Node Pools is now available in Azure Kubernetes Services. With Virtual Machines node pools, Azure Kubernetes Services directly manages the provisioning and bootstrapping of every single node - so you can, for example, mix VM SKUs (of a similar family) in a node pool.

## Azure Load Balancer

- [Load Balancer Health Event Logs (GA)](https://azure.microsoft.com/en-gb/updates?id=481818) : With [Azure Load Balancer health event logs](https://learn.microsoft.com/en-us/azure/load-balancer/load-balancer-health-event-logs), you can monitor the health of your load balancer, without having to set up and manage complex metric-based alerts or build a custom data ingestion pipeline. Logs can be [sent to a Log Analytics Workspace and queried there](https://learn.microsoft.com/en-us/azure/load-balancer/load-balancer-monitor-alert-health-event-logs).

## Azure Storage

- [Azure Storage Object Replication Metrics (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=484313) : Designed to provide users with [enhanced visibility and insights](https://learn.microsoft.com/en-us/azure/storage/blobs/object-replication-overview#replication-metrics) into their object replication progress (e.g. between blob containers, or (if I'm reading it right) across regions).

## Virtual Network Manager

- [Virtual Network Manager Network Verifier (GA)](https://azure.microsoft.com/en-gb/updates?id=484274) : This feature enables you to check if your network policies allow or disallow traffic between your Azure network resources. Quite a lot of power here as it can evaluate a number of different resources and policies - check out the [concept](https://learn.microsoft.com/en-gb/azure/virtual-network-manager/concept-virtual-network-verifier) and [how-to](https://learn.microsoft.com/en-gb/azure/virtual-network-manager/how-to-verify-reachability-with-virtual-network-verifier) documentation. Like the rest of VNM, [it isn't free](https://azure.microsoft.com/en-us/pricing/details/virtual-network-manager/#pricing); and currently GA in limited regions only (UK South but not UK West).