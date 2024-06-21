+++
title = 'Azure Snippets w/c 17/06/2024'
date = 2024-06-21T08:00:16+01:00
draft = false
categories = ['Azure Weekly 2024']
tags = ['DB for PostgreSQL', 'AKS', 'Compute', 'Virtual Network Manager', 'Azure SQL Managed Instance', 'ARM']
+++

Summary of Azure snippets for the week commencing 17th June 2024, grouped by Azure service. I managed to miss a week as the [Azure Updates](https://azure.microsoft.com/en-gb/updates/) site is currently undergoing maintenance (so the RSS feed isn't updating) and I've only just found its [temporary replacement](https://techcommunity.microsoft.com/t5/azure-updates/bg-p/AzureUpdates).

GA = Generally Available  
Public/Private Preview = as stated :-)

Azure services with highlighted updates this week:

- [Azure DB for PostgreSQL](#azure-db-for-postgresql)
- [Azure Kubernetes Service](#azure-kubernetes-service)
- [Azure Landing Zones](#azure-landing-zones)
- [Azure Resource Manager](#azure-resource-manager)
- [Azure SQL](#azure-sql)
- [Compute](#compute)
- [Virtual Network Manager](#virtual-network-manager)

## Azure DB for PostgreSQL

- [IOPS scaling for Flexible Server (GA)](https://techcommunity.microsoft.com/t5/azure-updates/week-of-june-20-2024-azure-updates/ba-p/4173016) : This feature empowers you to [dynamically scale your IOPS](https://learn.microsoft.com/en-us/azure/postgresql/flexible-server/concepts-storage#iops-scaling) based on your workload needs. Ensure optimal performance during high-demand operations like migrations or data loads and scale down to save costs when demand decreases.

## Azure Kubernetes Service

- [kube-egress-gateway (GA)](https://techcommunity.microsoft.com/t5/azure-updates/week-of-june-20-2024-azure-updates/ba-p/4173016) : [kube-egress-gateway](https://github.com/Azure/kube-egress-gateway) is an open-source project that offers a scalable and cost-efficient solution for configuring fixed source IPs for Kubernetes pod egress traffic on Azure.
- [OS Security Patch channel for Linux in AKS (GA)](https://techcommunity.microsoft.com/t5/azure-updates/week-of-june-20-2024-azure-updates/ba-p/4173016) : SecurityPatch now added to the [channels for node OS image upgrades](https://learn.microsoft.com/en-us/azure/aks/auto-upgrade-node-os-image?tabs=azure-cli#channels-for-node-os-image-upgrades) in AKS.
- [az command invoke in AKS (GA)](https://techcommunity.microsoft.com/t5/azure-updates/week-of-june-20-2024-azure-updates/ba-p/4173016) : [Invoke a command](https://learn.microsoft.com/en-us/azure/aks/access-private-cluster?tabs=azure-cli) (e.g. running kubectl) remotely in a private cluster through the AKS API, without connecting directly to the cluster. This can be done from a client that isn't on the cluster's private network. Access to the *command invoke* command is controlled through [RBAC permissions](https://learn.microsoft.com/en-us/azure/aks/access-private-cluster?tabs=azure-cli#before-you-begin).
- [AKS patch version 1.27.13 now available in AKS (GA)](https://github.com/Azure/AKS/releases/tag/2024-06-09)

## Azure Landing Zones

- [Zone Redundancy and Multi-Region Capabilities in Azure Landing Zones](https://techcommunity.microsoft.com/t5/azure-governance-and-management/announcing-zone-redundancy-and-multi-region-capabilities-in/ba-p/4170742) : Being integrated into Bicep and Terraform accelerators by EoY 2024.

## Azure Resource Manager

- [Change Actor (GA)](https://techcommunity.microsoft.com/t5/azure-governance-and-management/announcing-the-general-availability-of-change-actor/ba-p/4171801) : Identifying who made a change to your Azure resources and how the change was made just became easier! With Change Analysis, you can now see who initiated the change and with which client that change was made, for changes across all your tenants and subscriptions. Accessed via the [Azure Resource Graph](https://learn.microsoft.com/en-us/azure/governance/resource-graph/changes/get-resource-changes?tabs=azure-cli).

## Azure SQL

- [Advance Notifications for Managed Instance (GA)](https://techcommunity.microsoft.com/t5/azure-sql-blog/announcing-ga-of-advance-notifications-for-azure-sql-managed/ba-p/4171497) : [Get alerts for planned maintenance events](https://learn.microsoft.com/en-gb/azure/azure-sql/managed-instance/advance-notifications?view=azuresql) 24 hours ahead of time. Works with SQL Maintenance Windows. Configured via Service Health in the Azure Portal.

## Compute

- [Windows Server 2025 (Public Preview)](https://techcommunity.microsoft.com/t5/azure-updates/week-of-june-20-2024-azure-updates/ba-p/4173016) : Previewing Windows Server 2025 images for VMs

## Virtual Network Manager

- [Azure Virtual Network Manager mesh and direct connectivity (GA)](https://techcommunity.microsoft.com/t5/azure-updates/week-of-june-18-2024-azure-updates/ba-p/4170142) : [Deploy mesh or hub and spoke network topologies](https://learn.microsoft.com/en-us/azure/virtual-network-manager/concept-connectivity-configuration) for VNets through VMM without having to set up all the peerings manually.