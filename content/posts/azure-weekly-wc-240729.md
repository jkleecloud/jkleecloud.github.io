+++
title = 'Azure Snippets w/c 29/07/2024'
date = 2024-08-02T08:00:16+01:00
draft = false
categories = ['Azure Weekly 2024']
tags = ['Azure Backup', 'Azure Container Storage', 'AKS', 'Sustainability']
+++

Summary of Azure snippets for the week commencing 29th July 2024, grouped by Azure service.

GA = Generally Available  
Public/Private Preview = as stated :-)

Azure services with highlighted updates this week:

- [Azure Backup](#azure-backup)
- [Azure Container Storage](#azure-container-storage)
- [Azure Kubernetes Service](#azure-kubernetes-service)
- [Sustainability](#sustainability)

## Azure Backup

- [VM Backup support for Premium SSD v2 disks (GA)](https://learn.microsoft.com/en-gb/azure/backup/backup-support-matrix-iaas#vm-storage-support) : [Several updates around Premium SSD v2 and Ultra disks](https://azure.microsoft.com/en-us/blog/latest-advancements-in-premium-ssd-v2-and-ultra-azure-managed-disks/), but VM Backup now supporting them (and Ultra disks) with the Enhanced backup policy is probably the biggest update from my point of view. Note that cross-region and file-level restores (from a mounted disk) are still not supported. Also (importantly) note that you can't use geo-redundant (GRS) Recovery Services Vaults for enabling backup with Premium SSD v2 and Ultra disks.
- [Vaulted Backup for Azure Blob Storage (GA)](https://azure.microsoft.com/en-us/updates/v2/ga-vaulted-backup-azure-blob-storage) : Blob backups can now be stored in a Vault instead of just as snapshots in a Storage Account. Available in all public regions, but there are some [limitations](https://learn.microsoft.com/en-gb/azure/backup/blob-backup-support-matrix?tabs=vaulted-backup#limitations) to be aware of.

## Azure Container Storage

- [Azure Container Storage for Ephemeral (Local NVMe/Temp SSD) and Azure Disk (GA)](https://azure.microsoft.com/en-us/updates/v2/Azure-Container-Storage-GA) : ACS now ready for production workloads (ephemeral disks and Azure Disk-based ones, anyway). Lots of publicity for this one - [Azure Blog post](https://azure.microsoft.com/en-us/blog/embrace-the-future-of-container-native-storage-with-azure-container-storage/), [AKS Engineering blog post](https://azure.github.io/AKS/2024/07/30/azure-container-storage-ga), [documentation](https://learn.microsoft.com/en-gb/azure/storage/container-storage/).

## Azure Kubernetes Service

- [OS SKU in-place migration for AKS (GA)](https://azure.microsoft.com/en-us/updates/v2/OS-SKU-in-place-migration-for-AKS) : The [OS SKU in-place migration](https://learn.microsoft.com/en-gb/azure/azure-linux/tutorial-azure-linux-migration?tabs=azure-cli#in-place-os-sku-migration) feature allows you to trigger a node image upgrade between one Linux SKU (i.e. Ubuntu) to another (i.e. Azure Linux) on an existing nodepool. No need to create new nodes, cordon and drain the existing ones, and then delete them - the upgrade can roll through the cluster without having to create new node pools.

## Sustainability

- [Azure Carbon Optimization (Public Preview)](https://azure.microsoft.com/en-us/updates/v2/Carbon-Optimization) : Sustainability is still very much a hot topic with cloud workloads. [Carbon optimization](https://learn.microsoft.com/en-us/azure/carbon-optimization/) joins the [emissions dashboard](https://www.microsoft.com/en-us/sustainability/emissions-impact-dashboard) and [emissions insights](https://learn.microsoft.com/en-us/industry/sustainability/sustainability-data-solutions-azure-emissions-insights) (another preview service) to allow you to get a full picture of your cloud deployment impact and where it could be improved.