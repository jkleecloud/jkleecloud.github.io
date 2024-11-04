+++
title = 'Azure Snippets w/c 28/10/2024'
date = 2024-11-04T11:00:16+00:00
draft = false
categories = ['Azure Weekly 2024']
tags = ['API Center', 'APIM', 'Azure Storage', 'IaC']
+++

Summary of Azure snippets for the week commencing 28th October 2024, grouped by Azure service.

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [API Center](#api-center)
- [Azure Storage](#azure-storage)
- [Compute](#compute)
- [Infrastructure as Code](#infrastructure-as-code)

## API Center

- [API Management & API Center Synchronization (Public Preview)](https://azure.microsoft.com/en-us/updates/v2/API-Management-API-Center-Synchronization) : [Link an APIM instance to API Center](https://learn.microsoft.com/en-gb/azure/api-center/synchronize-api-management-apis?tabs=portal) to sync the API inventory and keep it continuously up to date.

## Azure Storage

- [Live Resize for Azure Premium SSD v2 and Ultra Disks (GA)](https://azure.microsoft.com/en-us/updates/v2/Live-Resize-for-Azure-Premium-SSD-v2-and-Ultra-Disks1) : Increase your Premium SSD v2 and Ultra disks' storage capacity without stopping your VM. Some limitations to this capability and unsupported regions, check the [docs](https://learn.microsoft.com/en-us/azure/virtual-machines/windows/expand-os-disk#expand-without-downtime) carefully.

## Compute

- [Azure Cobalt 100-based Virtual Machines (GA)](https://azure.microsoft.com/en-us/blog/azure-cobalt-100-based-virtual-machines-are-now-generally-available/) : General purpose Dpsv6-series and Dplsv6-series and memory-optimized Epsv6-series VM series. These VMs run on Microsoft’s first 64-bit Arm-based Azure Cobalt 100 CPU, which has been fully designed in-house. Up to 50% better price performance than previous generation Arm-based VMs. Region availability expanding through the rest of 2024, UK South is coming soon.
    - [Arm newsroom post](https://newsroom.arm.com/blog/arm-powered-microsoft-azure-cobalt-100-vms)


## Infrastructure as Code

- [AzAPI version 2.0 released (GA)](https://techcommunity.microsoft.com/t5/azure-tools-blog/announcing-azapi-2-0/ba-p/4275733) : The [AzAPI provider](https://registry.terraform.io/providers/Azure/azapi/latest/docs) is designed to expedite the integration of new Azure services with HashiCorp Terraform. It functions as a lightweight layer atop the Azure ARM REST APIs, and is a first class provider experience along with the [AzureRM provider](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs). Azure resources that might not yet be or may never be supported in AzureRM can be accessed by this provider, including private/public preview services and features. v2.0 now fully supports HCL (no more JSON) among other updates. Both [Microsoft](https://techcommunity.microsoft.com/t5/azure-tools-blog/unlocking-the-best-of-azure-with-azurerm-and-azapi-providers/ba-p/4283264) and [Hashicorp](https://www.hashicorp.com/blog/enhancing-azure-deployments-with-azurerm-and-azapi-terraform-providers) have blog posts comparing AzureRM and AzAPI and scenarios where you might choose one over the other (they're mostly the same post but with some additional stuff in each :-) There is also now a tool ([aztfmigrate](https://github.com/Azure/aztfmigrate)) that lets you migrate resources between the two providers. 