+++
title = 'Azure Snippets w/c 16/09/2024'
date = 2024-09-20T08:00:16+01:00
draft = true
categories = ['Azure Weekly 2024']
tags = ['IaC', 'Azure Storage', 'AKS']
+++

Summary of Azure snippets for the week commencing 16th September 2024, grouped by Azure service.

GA = Generally Available  
Public/Private Preview = as stated :-)

Azure services with highlighted updates this week:

- [Azure Kubernetes Service](#azure-kubernetes-service)
- [Azure Storage](#azure-storage)
- [Infrastructure as Code](#infrastructure-as-code)

## Azure Kubernetes Service

- [Latest AKS release (GA)](https://github.com/Azure/AKS/releases/tag/2024-08-27) : The latest release has almost finished its rollout:
    - AKS v1.27 is now deprecated - long-term support only
    - New versions of KEDA addon deployed

## Azure Storage

- [Live Resize for Azure Premium SSD v2 and Ultra Disks (Public Preview)](https://azure.microsoft.com/en-us/updates/v2/Live-Resize-for-Azure-Premium-SSD-v2-and-Ultra-Disks) : Dynamically increase the storage capacity of your Premium SSD v2 and Ultra disks [without causing any disruption to your applications](https://learn.microsoft.com/en-us/azure/virtual-machines/windows/expand-os-disk#expand-without-downtime). Still has some significant limitations and is only available in select regions at present.

## Infrastructure as Code

 - [Terraform AzureRM provider 4.0 (GA)](https://www.hashicorp.com/blog/terraform-azurerm-provider-4-0-adds-provider-defined-functions) : [This version](https://registry.terraform.io/providers/hashicorp/azurerm/latest) includes new capabilities to improve the extensibility and flexibility of the provider: provider-defined functions and improved resource provider registration. 