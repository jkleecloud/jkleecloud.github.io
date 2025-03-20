+++
title = 'Azure Snippets w/c 17/03/2025'
date = 2025-03-21T08:00:10Z
draft = true
categories = ['Azure Weekly 2025']
tags = ['AKS']
+++

Summary of Azure snippets for the week commencing 17th March 2025, grouped by Azure service. Notably, the AKS updates this time include a pretty significant networking retirement.

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [Application Gateway](#application-gateway)

## Azure Kubernetes Services

- [Kubenet networking for AKS to be retired in March 2028 (RET)](https://azure.microsoft.com/en-gb/updates?id=485172) : On March 31, 2028, kubenet networking for Azure Kubernetes Service (AKS) will be retired. CNI overlay networking is now the way forward if you want to do kubenet-style networking in AKS - MS have [instructions for migrating your AKS clusters to CNI overlay](https://learn.microsoft.com/en-gb/azure/aks/upgrade-aks-ipam-and-dataplane). If you use kubenet networking in your AKS clusters, I'd recommend starting to plan a migration as soon as possible.

- [Azure CNI powered by Cilium Node Subnet support in AKS (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=482225) : This enhancement allows users to configure AKS clusters with Azure CNI powered by Cilium and Node Subnet. Thereby, it extends compatibility of Cilium’s eBPF dataplane to all supported IP address management configurations on AKS clusters.