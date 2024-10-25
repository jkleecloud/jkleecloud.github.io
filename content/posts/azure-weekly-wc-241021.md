+++
title = 'Azure Snippets w/c 21/10/2024'
date = 2024-10-25T14:28:50+01:00
draft = false
categories = ['Azure Weekly 2024']
tags = ['FinOps', 'Azure Backup', 'Compute', 'Redis', 'Azure Storage']
+++

Summary of Azure snippets for the week commencing 21st October 2024, grouped by Azure service.

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [Azure Backup](#azure-backup)
- [Azure Storage](#azure-storage)
- [Compute](#compute)
- [FinOps](#finops)
- [Redis](#redis)

## Azure Backup

- [GRS and Cross-Region Restore support for Azure VMs using Premium SSD v2 and Ultra Disk in Azure Backup (GA)](https://azure.microsoft.com/en-us/updates/v2/AzBackupGrsForPv2Ultra) : Definite improvement for DR resilience if you're using Premium SSD v2 or Ultra disks with your VMs. GRS vaults and Cross-Region Restore are currently supported in the following regions for machines using Premium SSDv2 Disks: Southeast Asia, East Asia, North Europe, West Europe, East US, West US, and West US 3. Coming to other regions in later months (not sure this really counts as 'Generally Available' yet, if I'm being honest!).

- [Immutable Write Once Read Many (WORM) Storage for Backups in Azure Recovery Services Vaults (Public Preview)](https://azure.microsoft.com/en-us/updates/v2/Immutable-WORM-Storage-for-Backups-in-Azure-Recovery-Services-Vaults) : Azure Backup users will now have immutable WORM storage for their backups when [immutability is enabled and locked on a Recovery Services Vault](https://learn.microsoft.com/en-us/azure/backup/backup-azure-immutable-vault-concept?tabs=recovery-services-vault). When immutability is enabled, it ensures that a Recovery Point, once created, cannot be deleted or have its retention period reduced before its intended expiry. Now, when immutability is locked, Azure Backup will also use WORM-enabled immutable storage to meet any compliance requirements. This feature is applicable to both existing and new vaults with locked immutability. It is currently in preview in limited regions (no indication in the docs yet which regions those are, unfortunately). 

## Azure Storage

- [Storage account default egress limit increase to 200 Gbps (GA)](https://azure.microsoft.com/en-us/updates/v2/Storage-account-default-egress-limit-increase-to-200-Gbps) : The default maximum egress for general-purpose v2 and Blob storage accounts has been increased from 120 Gbps to 200 Gbps, in multiple regions including UK South (though not UK West). Applies to all new and existing storage accounts.

## Compute

- [VM Watch for Azure VMs (Public Preview)](https://azure.microsoft.com/en-us/updates/v2/VM-watch-on-Azure-VMs) : VM watch, now in preview, is a standardised, lightweight, and adaptable in-VM service offering for virtual machines and virtual machine scale sets. Enhanced VM health monitoring and checking, metric and log collection delivered via the [Application Health VM extension](https://learn.microsoft.com/en-us/azure/virtual-machines/extensions/health-extension?tabs=rest-api). No additional cost for it (at the moment at least).

## FinOps

- [FinOps Toolkit v0.6 (GA)](https://azure.microsoft.com/en-us/updates/v2/FinOps-toolkit-0-6-September-2024) : In September, the FinOps toolkit 0.6 added [a new library for FinOps best practices](https://techcommunity.microsoft.com/t5/finops-blog/unlocking-azure-savings-introducing-the-finops-best-practices/ba-p/4261450), new Power BI reports for governance and workload optimisation, support for all Cost Management datasets in FinOps hubs, [and more](https://techcommunity.microsoft.com/t5/finops-blog/what-s-new-in-finops-toolkit-0-6-september-2024/ba-p/4266301). Latest reports also include the ability to extract specific tags - very useful for custom reporting.

## Redis

- [In-place scaling for Enterprise Redis caches (GA)](https://azure.microsoft.com/en-us/updates/v2/In-place-scaling-for-Enterprise-caches) : Enterprise and Enterprise Flash tier caches now have the ability to [scale up or out](https://learn.microsoft.com/en-gb/azure/azure-cache-for-redis/cache-how-to-scale?tabs=scale-up-and-down-with-basic-standard-and-premium#how-to-scale-up-and-out---enterprise-and-enterprise-flash-tiers) without requiring downtime. Note that you can't scale down or scale in an Enterprise Redis cache as yet - so scale with care!
