+++
title = 'Azure Snippets w/c 10/02/2025'
date = 2025-02-13T08:00:10Z
draft = true
categories = ['Azure Weekly 2025']
tags = ['Azure Data Studio', 'Compute', 'AKS']
+++

Rather belated happy new year, and welcome to the first post of 2025!

Summary of Azure snippets for the week commencing 10th February 2025, grouped by Azure service.

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [Azure Data Studio](#azure-data-studio)
- [Azure Kubernetes Services](#azure-kubernetes-services)
- [Compute](#compute)

## Azure Data Studio

- [Azure Data Studio retiring on 28th February 2026 (RET)](https://azure.microsoft.com/en-gb/updates?id=479933) : [ADS is deprecated from February 2025](https://learn.microsoft.com/en-gb/azure-data-studio/whats-happening-azure-data-studio) - Visual Studio Code with the MSSQL extension is the database development tool of choice going forward. SQL Server Management Studio will remain available to handle any incompatibility issues.

## Azure Kubernetes Services

- [AKS Communication Manager (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=471275) : AKS Communication Manager simplifies notifications for all your AKS maintenance tasks by leveraging Azure Resource Notification and Azure Resource Graph frameworks. It provides timely alerts on event triggers and outcomes, allowing you to closely monitor your upgrades. In case of maintenance failures, it notifies you with the reasons for the failure, reducing operational hassles related to observability and follow-ups. It is a bit more 'DIY' than the annoucement suggests - you have to [build a Logic App](https://learn.microsoft.com/en-us/azure/aks/aks-communication-manager) and then hook it in to the ARN maintenance alerts.
- [Parallel image pulls by default in AKS (GA)](https://azure.microsoft.com/en-gb/updates?id=471237) : By default, AKS versions earlier than 1.31 use serialized image pulls. Starting with AKS version 1.31 preview, AKS defaults to parallel image pulls, which are [generally more performant](https://learn.microsoft.com/en-gb/troubleshoot/azure/azure-kubernetes/availability-performance/container-image-pull-performance).
- [IMDS restriction support (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=471270) : Currently, all pods on AKS nodes can access the AKS worker node's Azure Instance Metadata Service (IMDS) endpoint. AKS now offers a managed solution that [restricts IMDS endpoint access](https://learn.microsoft.com/en-gb/azure/aks/imds-restriction) for customer pods. Only AKS system pods and user pods with host network can access IMDS for retrieving information or authentication. Good enhancement to the security of your AKS clusters.

## Compute

- Azure Dl/D/E v6 VMs (GA) : Higher performance than previous generations, [Azure Boost](https://learn.microsoft.com/en-us/azure/azure-boost/overview) built-in including a new [Microsoft Azure Network Adapter](https://learn.microsoft.com/en-us/azure/virtual-network/accelerated-networking-mana-overview), [NVMe interface](https://learn.microsoft.com/en-us/azure/virtual-machines/nvme-overview) for disks to boost storage performance. Naturally, these are great for AI workloads :-) Avaialble in UK South but not UK West as yet.

