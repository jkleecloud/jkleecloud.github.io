+++
title = 'Azure Snippets w/c 08/09/2025'
date = 2025-09-11T08:00:16+01:00
draft = false
categories = ['Azure Weekly 2025']
tags = ['APIM', 'App Service', 'Application Gateway', 'Azure Functions', 'AKS', 'Service Groups', 'Azure Storage', 'Compute', 'Logic Apps', 'Virtual Networks']
+++

Summary of Azure snippets for the week commencing 8th September 2025, grouped by Azure service. Back to more normal posting after a bit of time off!

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [API Management](#api-management)
- [App Service](#app-service)
- [Application Gateway](#application-gateway)
- [Azure Functions](#azure-functions)
- [Azure Kubernetes Services](#azure-kubernetes-services)
- [Azure Service Groups](#azure-service-groups)
- [Azure Storage](#azure-storage)
- [Compute](#compute)
- [Logic Apps](#logic-apps)
- [Virtual Networks](#virtual-networks)

## API Management

- [Gateway level metrics and native autoscaling for Azure API Management v2 tiers (GA)](https://azure.microsoft.com/en-us/updates?id=501829) : Available for Azure API Management v2 tiers: Basic v2, Standard v2, and Premium v2. These updates give you [deeper visibility into gateway performance and enable automatic scaling](https://techcommunity.microsoft.com/blog/integrationsonazureblog/autoscaling-now-available-in-azure-api-management-v2-tiers/4424484) based on real-time usage. Gateway-level metrics include CPU and memory usage per gateway instance, providing the insights needed for monitoring, diagnostics, and intelligent scaling. With these metrics, you can define autoscale rules in Azure Monitor to automatically increase or decrease gateway instances, ensuring consistent performance without manual intervention. Autoscaling helps maintain reliability during traffic spikes, improves operational efficiency, and optimizes costs by scaling in when demand drops.

 - [Workspaces and workspace gateways in the Premium v2 tier (GA)](https://azure.microsoft.com/en-us/updates?id=501809) : (Note: while the workspaces feature is GA, the Premium v2 tier itself is still in Preview!) [Workspaces](https://techcommunity.microsoft.com/blog/integrationsonazureblog/workspaces-are-now-generally-available-in-azure-api-management-premium-v2/4435589) enable organizations to manage and govern APIs at scale. They make it easier to support large portfolios across teams or business units, while [maintaining central governance, observability, and security](https://learn.microsoft.com/en-gb/azure/api-management/workspaces-overview).

 ## App Service

 - [New Premium v4 Offering (GA)](https://azure.microsoft.com/en-us/updates?id=500374) : The new [Premium v4 offering](https://techcommunity.microsoft.com/blog/appsonazureblog/announcing-general-availability-of-premium-v4-for-azure-app-service/4446204) provides faster processors, NVMe local storage, and memory-optimized options, running on the latest Azure hardware. Premium v4 is available for both Windows and Linux customers, and includes sizes starting from 1 vCPU and 4GB of memory all the way up to 32 vCPU and 256GB memory. And you should be able to save money even using PAYG :-) Select regions only at present - presumably this will expand quickly.

 ## Application Gateway

- [MaxSurge support for zero-capacity-impact upgrades (GA)](https://azure.microsoft.com/en-us/updates?id=501017) : Azure Application Gateway [now supports MaxSurge](https://learn.microsoft.com/en-us/azure/application-gateway/application-gateway-faq#maintenance), enabling new instances to be provisioned during rolling upgrades without taking existing ones offline. This allows customers to transition to newer gateway versions without any capacity degradation.

## Azure Functions

- [Flex Consumption plan now supports 512 MB instance size and diagnostic settings (GA)](https://azure.microsoft.com/en-us/updates?id=500369) : Azure Functions now allows you to choose 512 MB in addition to 2048 MB and 4096 MB as the memory instance size for your Flex Consumption apps. This enables you to further cost-optimize your apps that require fewer resources, and allows your apps to scale out further within the default quota. Diagnostic settings allow you to collect Flex Consumption application logs and resource metrics, then send to different destinations like Log Analytics, storage account, event hub, or partner solutions for monitoring and analysis. 

## Azure Kubernetes Services

- [AKS Release 2025-08-29 now available (GA)](https://github.com/Azure/AKS/releases/tag/2025-08-29) : This release sees [AKS Automatic](https://learn.microsoft.com/en-gb/azure/aks/intro-aks-automatic) go GA ([launch event](https://developer.microsoft.com/en-us/reactor/events/26173/) on 16th September); AKS patch versions 1.33.3, 1.32.7, and 1.30.11 are now available; and the Istio service mesh add-on is now compatible with AKS long-term support for Istio revisions asm-1-25+ and AKS versions 1.28+.

- [Connect to private AKS clusters with Azure Bastion (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=500996) : Coming fairly hot on the heels of the initial preview release allowing connectivity to AKS, with this release, you can now establish a secure tunnel from your local machine — via Azure Bastion — directly to your AKS API server using your standard Kubernetes tooling. This enables seamless access to both [private clusters](https://learn.microsoft.com/en-us/azure/bastion/bastion-connect-to-aks-private-cluster) and public clusters with API server authorized IP ranges. Brings another access path into Bastion for which you would previously have needed a jump box of some sort.

- [CNI Overlay for Application Gateway for Containers and AGIC (GA)](https://azure.microsoft.com/en-us/updates?id=485357) : [Application Gateway for Containers](https://learn.microsoft.com/en-gb/azure/application-gateway/for-containers/container-networking#cni-overlay-and-application-gateway-for-containers) and Application Gateway Ingress Controller (AGIC) now support CNI overlay networking in AKS.

## Azure Service Groups

- [Service Groups (Public Preview)](https://techcommunity.microsoft.com/blog/azuregovernanceandmanagementblog/announcing-public-preview-for-azure-service-groups/4446572) : [Service Groups](https://learn.microsoft.com/en-gb/azure/governance/service-groups/overview) are a new resource container enabling management and observability scenarios where flexibility in hierarchy and membership is needed. Service Groups are tenant-level resources so they can have members across the tenant but do not interfere with or use tenant-wide RBAC or Policy abilities. They exist alongside but separate from other ARM groupings (Management Groups, Resource Groups), don't manage Policy or RBAC and need minimal permissions - looks like they may be a way of surfacing application resource grouping and monitoring flexibly in e.g. Azure Monitor (or Cost Management?) when the resource deployments for the application cross multiple other ARM groups.

## Azure Storage

- [Operating System (OS) Disks on Standard HDD will be retired on 08 September 2028 (RET)](https://azure.microsoft.com/en-us/updates?id=500157) : Look to [convert any managed OS disks](https://learn.microsoft.com/en-us/azure/virtual-machines/disks-convert-types?tabs=azure-powershell) still on Standard HDD to one of the SSD tiers before the [retirement date](https://learn.microsoft.com/en-us/azure/virtual-machines/disks-hdd-os-retirement). Managed data disks using Standard HDD are not affected.

- [File share-centric management model for Azure Files (Public Preview)](https://azure.microsoft.com/en-us/updates?id=503096) : This feature makes [a File Share a top-level resource](https://techcommunity.microsoft.com/blog/azurestorageblog/simplifying-file-share-management-and-control-for-azure-files/4452634) in Azure, so you can manage it without having to worry about managing the storage account underneath (much like how managed disks work for Azure Disks). Utilising the provisioned v2 billing model (which is now [GA for the SSD (premium) tier](https://azure.microsoft.com/en-us/updates?id=500695) as well as Standard), capacity and throughput can be provisioned for the File Share directly rather than having to work through the underlying storage account, and costs can now be attributed directly to it (useful for departmental charging). Currently available in very limited regions (includes North Europe, but not UK).

## Compute

- [Upgrade existing Azure Gen 1 VMs to Gen 2 - Trusted launch (GA)](https://azure.microsoft.com/en-us/updates?id=499104) : There is now an [in-place upgrade path](https://techcommunity.microsoft.com/blog/azurecompute/increase-security-for-azure-vms-trusted-launch-in-place-upgrade-support-now-avai/4440584) for Gen 1 VMs (and Uniform scale sets - Flex are in preview) to Gen 2 with Trusted Launch (note: both of the latter come together, you can't upgrade to Gen 2 without Trusted Launch via this method). Check [the docs](https://learn.microsoft.com/en-gb/azure/virtual-machines/trusted-launch-existing-vm-gen-1?tabs=windows%2Cpowershell) first to ensure your VMs fit the prerequisites - notably, despite Windows Server 2016 being supported for Trusted Launch, it doesn't support this upgrade path (it doesn't support the utility needed to upgrade Master Boot Record (MBR) disks to GUID Partition Table (GPT)) and you have to go to WS2019 or 2022 first.

## Logic Apps

- [Logic Apps Hybrid Deployment Model (GA)](https://azure.microsoft.com/en-us/updates?id=501824) : You can now host Logic Apps on customer-managed infrastructure, including on-premises, private cloud, or third-party public cloud environments. This [deployment model](https://techcommunity.microsoft.com/blog/integrationsonazureblog/announcement-general-availability-of-logic-apps-hybrid-deployment-model/4422414) helps organizations meet regulatory, data privacy, and network requirements while still leveraging the capabilities of Azure Logic Apps. It supports a semi-connected architecture with local workflow processing, storage, and network access, enabling higher throughput and direct access to local data sources. GA release also includes Open Telemetry support and is available in UK South.

## Virtual Networks

- [Multiple address prefixes for subnets (GA)](https://azure.microsoft.com/en-us/updates?id=502583) : Previously Azure Virtual Network subnets supported only a single address prefix, which limited the scale out for certain applications when the address space was exhausted. This capability now permits [additional address prefixes to be added to the subnet](https://learn.microsoft.com/en-us/azure/virtual-network/how-to-multiple-prefixes-subnet?tabs=powershell), expanding the available address space without the need to empty the subnet to resize. The key benefits of this approach are: Dynamic subnet expansion without impacting existing workloads in subnet; Efficient subnet address space usage with scope for expansion when needed.