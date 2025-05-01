+++
title = 'Azure Snippets w/c 28/04/2025'
date = 2025-05-02T08:00:16+01:00 (BST)
draft = true
categories = ['Azure Weekly 2025']
tags = ['DB for PostgreSQL', 'Redis', 'IaC', 'NSG', 'Application Gateway', 'Azure Backup', 'Virtual Network Manager', 'Compute', 'FinOps', 'Azure Storage']
+++

Summary of Azure snippets for the week commencing 28th April 2025, grouped by Azure service.

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [API Management](#api-management)
- [Azure Kubernetes Services](#azure-kubernetes-services)
- [Azure SQL](#azure-sql)
- [Compute](#compute)
- [Sustainability](#sustainability)
- [Virtual Networks](#virtual-networks)

## API Management

- [Service Update Configuration for Azure API Management (GA)](https://azure.microsoft.com/en-gb/updates?id=490737) : [Service update settings](https://learn.microsoft.com/en-us/azure/api-management/configure-service-update-settings) for Azure API Management give greater control over when and how APIM instances receive platform updates — including new features, security patches, and reliability improvements. Select an update group to control how early in the rollout cycle an instance receives updates, and configure custom maintenance windows for updates to occur. This can allow configuration of canary deployments for APIM.

- [Inbound Private Endpoint for Azure API Management Standard v2 (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=490732) : Brings [Private Endpoint connectivity to the Standard v2 tier of APIM](https://techcommunity.microsoft.com/blog/integrationsonazureblog/announcing-open-public-preview-of-inbound-private-endpoint-for-standard-v2-tier-/4402521). Still only protects the Gateway endpoint though. Additionally, Azure Front Door Premium can now connect privately to API Management instances (Standard v2 and classic v1 tiers) using Private Link.

## Azure Kubernetes Services

- [Network isolated cluster in AKS (GA)](https://azure.microsoft.com/en-gb/updates?id=491427) : AKS now provides the option to use [network isolated clusters](https://learn.microsoft.com/en-us/azure/aks/concepts-network-isolated) to simplify the process of restricting network access and reduce the risk of unintentional exposure of the cluster's public endpoints to prevent security breaches. Permits control of outbound/egress traffic from the cluster without needing to put a firewall in the path.

## Azure SQL

- [I/O Performance Analysis — SQL Server on Azure Virtual Machines (GA)](https://azure.microsoft.com/en-gb/updates?id=487453) : Accessible in the Azure portal, this feature helps you optimise your SQL Server workloads by [identifying I/O performance bottlenecks](https://learn.microsoft.com/en-gb/azure/azure-sql/virtual-machines/windows/storage-performance-analysis?view=azuresql) caused by virtual machine (VM) or disk throttling. Additionally, when you need to track I/O-related best practices, you can execute a small subset of the SQL Server best practices assessment rules against your SQL Server instance and use historical data to analyze the latest results. (Not strictly 'Azure SQL', more 'SQL on Azure', but it fits my tagging better this way :-)

## Compute

- [Azure Compute Fleet (GA)](https://azure.microsoft.com/en-gb/updates?id=490327) : Another addition to the 'Fleet' services (joining AKS Fleet Manager) for large-scale resource management, [Azure Compute Fleet](https://learn.microsoft.com/en-us/azure/azure-compute-fleet/overview) allows users to [easily obtain large amounts of compute capacity](https://techcommunity.microsoft.com/blog/azurecompute/azure-compute-fleet---generally-available/4408859), algorithmically mixing and matching a variety of available and VM sizes suitable to a user's workload; up to 10,000 VMs in a single fleet.

## Sustainability

- [New Enhancements to Carbon Optimization (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=488052) : [Carbon optimization in Azure](https://learn.microsoft.com/en-us/azure/carbon-optimization/) now includes new capabilities to improve visibility into cloud emissions data. Enhancements include expanded API limits, extended role-based access, and new filtering options for better analysis.

## Virtual Networks

- [Subnet Peering (GA)](https://techcommunity.microsoft.com/blog/azurenetworkingblog/introducing-subnet-peering-in-azure/4383841) : Allows connection of two virtual networks by peering together subnet address spaces instead of the entire VNet. This could be very powerful if you have a secure/restricted network scenario - it can dramatically limit the routing exposed across the VNets. While this is available in all regions, you'll need to register your subscription to enable it; and it can currently be configured via scripting (Terraform, ARM, Azure CLI, PowerShell) but not through the Portal. The same considerations about non-overlapping address spaces apply as with VNet peering, and there are other limitations and consideration to take into account - check [the documentation](https://learn.microsoft.com/en-us/azure/virtual-network/how-to-configure-subnet-peering) and Azure Networking [blog](https://techcommunity.microsoft.com/blog/azurenetworkingblog/introducing-subnet-peering-in-azure/4383841) [posts](https://techcommunity.microsoft.com/blog/azurenetworkingblog/subnet-peering/4397640) for more details.

- [Azure virtual network terminal access point (TAP) (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=490830) : The [Virtual Network TAP](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-tap-overview) enables customers to continuously stream virtual machine network traffic to a network packet collector or analytics tool (an NVA such as F5 or Barracuda). Unlike traditional packet capture solutions that require the deployment of additional agents or network appliances, virtual network TAP leverages Azure’s native infrastructure to mirror traffic with minimal overhead, enhancing both analytics and security capabilities.

- [Increased VNet limits for Private Endpoints (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=487406) : With [High Scale Private Endpoints](https://learn.microsoft.com/en-us/azure/private-link/increase-private-endpoint-vnet-limits?tabs=ARG-HSP-Powershell%2Cvalidate-portal), you are now able to increase Azure Private Endpoint’s default limits (1000 endpoints in a singular VNet) for local and peered virtual networks. This will raise private endpoint default limits to 5,000 in a singular VNet and 20,000 across your peered virtual networks. Currently only available in a [small subset of regions](https://learn.microsoft.com/en-us/azure/private-link/increase-private-endpoint-vnet-limits?tabs=ARG-HSP-Powershell%2Cvalidate-portal#limitations) (including UK South).



