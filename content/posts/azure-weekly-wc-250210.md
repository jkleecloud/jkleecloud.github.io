+++
title = 'Azure Snippets w/c 10/02/2025'
date = 2025-02-13T08:00:10Z
draft = false
categories = ['Azure Weekly 2025']
tags = ['Azure Data Studio', 'Compute', 'AKS', 'Virtual Network Manager', 'Azure SQL', 'Azure SQL Managed Instance', 'Azure Storage', 'IaC']
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
- [Azure SQL](#azure-sql)
- [Azure Storage](#azure-storage)
- [Azure Virtual Network Manager](#azure-virtual-network-manager)
- [Compute](#compute)
- [Infrastructure as Code](#infrastructure-as-code)

## Azure Data Studio

- [Azure Data Studio retiring on 28th February 2026 (RET)](https://azure.microsoft.com/en-gb/updates?id=479933) : [ADS is deprecated from February 2025](https://learn.microsoft.com/en-gb/azure-data-studio/whats-happening-azure-data-studio) - Visual Studio Code with the MSSQL extension is the database development tool of choice going forward. SQL Server Management Studio will remain available to handle any incompatibility issues.

## Azure Kubernetes Services

- [AKS Communication Manager (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=471275) : AKS Communication Manager simplifies notifications for all your AKS maintenance tasks by leveraging Azure Resource Notification and Azure Resource Graph frameworks. It provides timely alerts on event triggers and outcomes, allowing you to closely monitor your upgrades. In case of maintenance failures, it notifies you with the reasons for the failure, reducing operational hassles related to observability and follow-ups. It is a bit more 'DIY' than the annoucement suggests - you have to [build a Logic App](https://learn.microsoft.com/en-us/azure/aks/aks-communication-manager) and then hook it in to the ARN maintenance alerts.
- [Parallel image pulls by default in AKS (GA)](https://azure.microsoft.com/en-gb/updates?id=471237) : By default, AKS versions earlier than 1.31 use serialized image pulls. Starting with AKS version 1.31 preview, AKS defaults to parallel image pulls, which are [generally more performant](https://learn.microsoft.com/en-gb/troubleshoot/azure/azure-kubernetes/availability-performance/container-image-pull-performance).
- [IMDS restriction support (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=471270) : Currently, all pods on AKS nodes can access the AKS worker node's Azure Instance Metadata Service (IMDS) endpoint. AKS now offers a managed solution that [restricts IMDS endpoint access](https://learn.microsoft.com/en-gb/azure/aks/imds-restriction) for customer pods. Only AKS system pods and user pods with host network can access IMDS for retrieving information or authentication. Good enhancement to the security of your AKS clusters.
- [New AKS Monitoring Experience (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=479448) : The [new Monitoring experience](https://techcommunity.microsoft.com/blog/azureobservabilityblog/public-preview-the-new-aks-monitoring-experience/4297181), updating Insights, provides both basic (free) and detailed insights (with enabled Prometheus metrics and logging), offering a unified, single-pane-of-glass experience. The basic experience is available for all AKS users with no configuration required at all.

## Azure SQL

- [Azure SQL DB Free offer (GA)](https://azure.microsoft.com/en-gb/updates?id=467778) : Try [10 Azure SQL Databases free of charge](https://learn.microsoft.com/en-us/azure/azure-sql/database/free-offer?view=azuresql) for the life of your subscription. With just a couple of clicks, you can power the application you want to build. This new offer provides 10 databases, each with 32 GB General Purpose, serverless Azure SQL database, and 100,000 vCore seconds of compute free every month. Available for any subscription type, free amount renews monthly.
- [Service Endpoint Policies for Managed Instances (GA)](https://techcommunity.microsoft.com/blog/azuresqlblog/service-endpoint-policies-for-azure-storage-now-generally-available-in-sql-manag/4366541) : Azure SQL Managed Instance now allows service endpoint policies for Azure Storage accounts, allowing you to deny your managed instances from accessing any storage account outside of a set of pre-approved ones. This security mechanism helps guard your data from unauthorized copying (data exfiltration) or configuration errors, like exporting production data to development accounts.

## Azure Storage

- [Azure Files provisioned v2 billing model for HDD (standard)](https://azure.microsoft.com/en-gb/updates?id=474894) (GA) : Brings the [provisioned v2 billing model](https://learn.microsoft.com/en-gb/azure/storage/files/understanding-billing#provisioned-v2-model) for Azure Files (allowing separate specification of storage, IOPS and throughput) to standard HDD-based storage. Available in UK South and UK West.

## Azure Virtual Network Manager

- [New Pricing for AVNM (GA)](https://azure.microsoft.com/en-gb/updates?id=480669) : Pricing has moved from a subscription-based model to VNet-based (charged by number of VNets where AVNM is deployed).

## Compute

- [6th Generation Intel-based VMs - Dv6/Ev6 (GA)](https://azure.microsoft.com/en-gb/updates?id=478996) : Higher performance than previous generations, [Azure Boost](https://learn.microsoft.com/en-us/azure/azure-boost/overview) built-in including a new [Microsoft Azure Network Adapter](https://learn.microsoft.com/en-us/azure/virtual-network/accelerated-networking-mana-overview), [NVMe interface](https://learn.microsoft.com/en-us/azure/virtual-machines/nvme-overview) for disks to boost storage performance. Naturally, these are great for AI workloads :-) Avaialble in UK South but not UK West as yet. [Blog post](https://techcommunity.microsoft.com/blog/azurecompute/announcing-general-availability-of-azure-dlde-v6-vms-powered-by-intel-emr-proces/4376186).
- [Upgrade Gen 1 VMs to Gen 2-Trusted Launch (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=481565) : Trusted Launch VMs provide foundational compute security to Azure Generation 2 VMs by enabling Secure Boot and vTPM capabilities. Trusted Launch capabilities protect OS against rootkits, boot kits and enables attestation by measuring the boot chain of VM. Make sure you check out the [documentation](https://learn.microsoft.com/en-gb/azure/virtual-machines/trusted-launch-existing-vm-gen-1?tabs=windows%2Cpowershell) if you're thinking of doing this - it's not recommended for Production workloads at the moment, and there are a lot of prerequisites and potential gotchas. Note also that you can create a new Gen 2 VM without Trusted Launch, but the upgrade only supports moving to Trusted Launch.

## Infrastructure as Code

- [Terraform Azure Verified Modules for Platform Landing Zone (ALZ) (GA)](https://techcommunity.microsoft.com/blog/azuretoolsblog/announcing-general-availability-of-terraform-azure-verified-modules-for-platform/4366027) : Terraform modules for deploying platform landing zones, along with their own Terraform provider. Seems to tie in with a big overhaul of [Azure Verified Modules](https://azure.github.io/Azure-Verified-Modules/) and [Landing Zone documentation](https://azure.github.io/Azure-Landing-Zones/) - check it all out!
