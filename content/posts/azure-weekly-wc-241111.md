+++
title = 'Azure Snippets w/c 11/11/2024'
date = 2024-11-13T16:00:12Z
draft = true
categories = ['Azure Weekly 2024']
tags = ['AKS', 'Azure Load Balancer', 'Azure Storage', 'Compute', 'Virtual Network Manager']
+++

Summary of Azure snippets for the week commencing 11th November 2024, grouped by Azure service.

The [new Azure updates](https://azure.microsoft.com/en-gb/updates/) page is now live (complete with RSS feed - why they could provide that for the updates but not for the new Tech Community platform blogs is a bit beyond me!). Some of the links this week use the old URL format, but they should still work.

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [Azure Kubernetes Service](#azure-kubernetes-service)
- [Azure Load Balancer](#azure-load-balancer)
- [Azure Storage](#azure-storage)
- [Compute](#compute)
- [Virtual Network Manager](#virtual-network-manager)

## Azure Kubernetes Service

- [Latest AKS release (GA)](https://github.com/Azure/AKS/releases/tag/2024-10-25) : Includes AKS patch versions 1.28.14, 1.29.9, 1.30.5 and GA for AKS 1.31; plus the first official patch version of AKS LTS 1.27, 1.27.100.
- [Advanced Container Networking Services (GA)](https://azure.microsoft.com/en-gb/updates?id=466985) : [ACNS](https://learn.microsoft.com/en-gb/azure/aks/advanced-container-networking-services-overview?tabs=cilium) includes Advanced Network Observability, providing pod-level metrics, DNS insights, and enhanced troubleshooting tools for network debugging in AKS, plus FQDN filtering. A [powerful upgrade to network observability in AKS](https://techcommunity.microsoft.com/blog/azureobservabilityblog/advanced-network-observability-for-your-azure-kubernetes-service-clusters-throug/4176736).
- [Delete a specific machine in a node pool (GA)](https://azure.microsoft.com/en-gb/updates?id=466990) : It is now possible to [specifically choose which VM to delete and remove](https://learn.microsoft.com/en-gb/azure/aks/manage-node-pools#remove-specific-vms-in-the-existing-node-pool) when scaling down a node pool in AKS. This provides greater control and flexibility in managing resources within the node pool. Actioned via the Azure CLI, and doesn't cordon and drain the node - need to do that yourself first.
- [Ignore PDBs on node deletion (GA)](https://azure.microsoft.com/en-gb/updates?id=466995) : Node pools in AKS can now be deleted even if there are pods monitored by a Pod Disruption Budget (PDB) – previously, the deletion of the node pool could fail due to an unsatisfied PDB. This enhancement allows the deletion to proceed by [ignoring the PDB error](https://learn.microsoft.com/en-gb/azure/aks/delete-node-pool?tabs=azure-cli#ignore-poddisruptionbudgets-pdbs-when-removing-an-existing-node-pool) that would previously block the deletion from continuing.
- [Static egress gateway (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=467018) : This feature allows AKS customers to configure a [fixed source IP](https://learn.microsoft.com/en-gb/azure/aks/configure-static-egress-gateway) for out-of-cluster communications without incurring the significant cost of deploying a dedicated node pool with a NAT gateway. Useful for connecting AKS clusters/host apps to external systems via a known outbound IP address.

## Azure Load Balancer

- [Azure cross-subscription Load Balancer (GA)](https://azure.microsoft.com/en-us/updates/v2/Generally-Available-Azure-cross-subscription-Load-Balancer) : [Cross-subscription load balancing](https://learn.microsoft.com/en-us/azure/load-balancer/cross-subscription-overview) enables the load balancer components to be located in different subscriptions. For example, the frontend IP address or the backend instances could be located in a different subscription from the one that the load balancer belongs to. Useful if your networking and application resources are in different subscriptions, for example. Available in all Azure public regions, China cloud regions, and Government cloud regions.
- [Load Balancer Health Status (GA)](https://azure.microsoft.com/en-us/updates/v2/generally-available-azure-load-balancer-now-supports-health-status) : Designed to provide detailed information about the health of backend instances in your Azure Load Balancer backend pool, the [Health Status](https://learn.microsoft.com/en-gb/azure/load-balancer/load-balancer-manage-health-status?tabs=azure-portal) feature offers valuable insights into the state of health of your backend instances and specific reasons for their health status, including user-triggered issues and platform-triggered reason codes. Good that ALB is [finally getting some more detailed monitoring](https://techcommunity.microsoft.com/blog/azurenetworkingblog/troubleshoot-health-probe-failures-with-azure-load-balancer-health-status/4287244)!
- [Administrative State (Admin State) (GA)](https://learn.microsoft.com/en-gb/azure/load-balancer/admin-state-overview) : Admin State enables you to override the health probe behavior for each instance without additional configuration changes to your Load Balancer such as changing network security rules or closing ports. This makes management, especially during maintenance, patching or testing, easy; allowing you to set instances as up or down and control connection behavior with no additional overhead. I can think of several past instances where this would have been useful! [Documentation](https://learn.microsoft.com/en-gb/azure/load-balancer/admin-state-overview) and [blog post](https://techcommunity.microsoft.com/blog/azurenetworkingblog/using-admin-state-to-control-your-azure-load-balancer-backend-instances/4155457).

## Azure Storage

- [Azure File Sync support for managed identities (Public Preview)](https://azure.microsoft.com/en-us/updates/v2/Azure-File-Sync-support-for-managed-identities) : Eliminates the need for [shared keys](https://learn.microsoft.com/en-gb/rest/api/storageservices/authorize-with-shared-key) as a method of authentication to your Azure file shares by [utilising a system-assigned managed identity](https://learn.microsoft.com/en-gb/azure/storage/file-sync/file-sync-managed-identities) provided by Microsoft Entra ID. A good move to improve security and make use of managed identities. Available in all Azure Public and Gov regions supported by Azure File Sync
- [Convert to Azure Premium SSD v2 disks (GA)](https://azure.microsoft.com/en-us/updates/v2/Convert-to-Azure-Premium-SSD-v2-disks) : This feature allows you to migrate your existing Standard SSD, Standard HDD, or Premium SSD v1 disks to Pv2 disks in a few clicks with minimal downtime. Very useful as it takes some of the pain out of such a migration, but there are some limitations - check [the docs](https://learn.microsoft.com/en-us/azure/virtual-machines/disks-convert-types?tabs=azure-powershell#convert-premium-ssd-v2-disks) carefully.

## Compute
- [Windows Server 2025 (GA)](https://www.microsoft.com/en-us/windows-server/blog/2024/11/04/windows-server-2025-now-generally-available-with-advanced-security-improved-performance-and-cloud-agility/) : Advanced security, improved performance, and cloud agility - check out the blog post for more detail.

## Virtual Network Manager

- V[irtual Network Manager user-defined route (UDR) management (GA)](https://azure.microsoft.com/en-us/updates/v2/Introducing-the-general-availability-of-Azure-Virtual-Network-Manager-UDR-management) : Hot on the heels of the [recently announced IP address management preview feature](https://jkleecloud.github.io/posts/azure-weekly-wc-240930/#virtual-network-manager), [UDR management](https://learn.microsoft.com/en-us/azure/virtual-network-manager/concept-user-defined-route) simplifies managing complex routing behaviors by automating UDR orchestration. Through Azure Virtual Network Manager’s UDR management, users can easily set up routing configurations that define routing rules, allowing automatic deployment across virtual networks. This means users no longer need to manually create UDRs or use custom scripts—reducing errors and simplifying routing at scale. [GA in specific regions](https://learn.microsoft.com/en-us/azure/virtual-network-manager/concept-user-defined-route#general-availability), including UK South and UK West. Centralising and automating UDR creation is definitely useful, particularly for big networks.
