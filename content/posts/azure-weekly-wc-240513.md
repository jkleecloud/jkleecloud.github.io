+++
title = 'Azure Snippets w/c 13/05/2024'
date = 2024-05-14T09:13:00+01:00
draft = true
categories = ['Azure Weekly 2024']
tags = ['AKS', 'Application Gateway']
+++

Summary of Azure snippets for the week commencing 13th May 2024, grouped by Azure service.

GA = Generally Available  
Public/Private Preview = as stated :-)

Azure services with highlighted updates this week:

- [Application Gateway](#application-gateway)
- [Azure Kubernetes Service](#azure-kubernetes-service)
- [Azure Site Recovery](#azure-site-recovery)

## Application Gateway

- [Application Gateway v2 Basic SKU (Public Preview)](https://azure.microsoft.com/en-gb/updates/public-preview-azure-application-gateway-v2-basic-sku/) : AG v2 gets a Basic SKU. Same base functionality and Capacity Units as Standard, with a slightly lower SLA (99.9% vs 99.95%), lower scaling maximums, and none of the advanced stuff (e.g. Private Link, URL rewrites). [SKU comparison here](https://learn.microsoft.com/en-us/azure/application-gateway/overview-v2#sku-types). Presumably the fixed cost will be cheaper (once it's out of preview :-)

## Azure Kubernetes Service

- [New version of AKS extension in Visual Studio Code](https://azure.microsoft.com/en-gb/updates/new-version-of-aks-extension-in-visual-studio-code-now-available/) : The [AKS extension in Visual Studio Code](https://github.com/Azure/vscode-aks-tools) has been updated to version 1.4.3. This new release includes general enhancements as well as a new command "Retina capture" (which uses the [Retina](https://retina.sh/) tool Microsoft recently open-sourced).
- [AKS automatic use of Zone-Redundant storage to create managed disks when AKS cluster is deployed across availability zones](https://github.com/Azure/AKS/releases/tag/2024-04-28) : With Kubernetes 1.29 and built-in storage classes. As ZRS is more expensive than LRS, [this can be overridden](https://learn.microsoft.com/en-us/azure/aks/concepts-storage#storage-classes) with a custom storage class.

## Azure Site Recovery
[ASR support for Trusted Launch VMs (Public Preview)](https://azure.microsoft.com/en-gb/updates/public-preview-azure-site-recovery-support-for-azure-trusted-launch-vms-windows-os/) : Fills a gap in ASR provision. [Few gotchas to check](https://learn.microsoft.com/en-us/azure/site-recovery/concepts-trusted-vm) though.