+++
title = 'Azure Snippets w/c 22/07/2024'
date = 2024-07-26T08:00:16+01:00
draft = false
categories = ['Azure Weekly 2024']
tags = ['AKS', 'DB for PostgreSQL', 'Azure Storage', 'Compute', 'Governance']
+++

Summary of Azure snippets for the week commencing 22nd July 2024, grouped by Azure service. The [Azure Updates](https://azure.microsoft.com/en-gb/updates/) site is working again, in its new v2 version, though the RSS feed isn't yet.

GA = Generally Available  
Public/Private Preview = as stated :-)

Azure services with highlighted updates this week:

- [Azure DB for PostgreSQL](#azure-db-for-postgresql)
- [Azure Kubernetes Service](#azure-kubernetes-service)
- [Azure Storage](#azure-storage)
- [Compute](#compute)
- [Governance](#governance)

## Azure DB for PostgreSQL

- [Major version upgrade support for PostgreSQL 16 (GA)](https://azure.microsoft.com/en-us/updates/v2/Major-version-upgrade-support-for-PostgreSQL16) : Azure Database for PostgreSQL - Flexible Server now supports [in-place major version upgrades](https://learn.microsoft.com/en-us/azure/postgresql/flexible-server/concepts-major-version-upgrade) to PostgreSQL 16. This update offers access to the latest PostgreSQL features with minimal downtime and a simplified upgrade process.

## Azure Kubernetes Service

- The [latest AKS release](https://github.com/Azure/AKS/releases/tag/2024-07-16) is now rolling out : 
    - AKS version 1.30 is now GA.
    - AKS patch versions 1.30.2, 1.30.1, 1.29.6, 1.28.11, 1.27.15, are now available (so check your cluster versions for any that now fall into 'N - 3' or lower).

## Azure Storage

- [Convert to Azure Premium SSD v2 disks (Public Preview)](https://azure.microsoft.com/en-us/updates/v2/convert-to-azure-premium-ssd-v2) : This feature allows you to migrate your existing Standard SSD, Standard HDD, or Premium SSD v1 disks to Pv2 disks in a few clicks with minimal downtime. This process avoids disk destruction, eliminates the need to use snapshots as a staging resource, and doesn’t require waiting for background data copying. Expands the [conversion capability](https://learn.microsoft.com/en-us/azure/virtual-machines/disks-convert-types?tabs=azure-powershell) and could be very useful if your workloads can take advantage of Premium SSD v2 capabilities - you had to create a new v2 SSD disk from a snapshot previously.

## Compute

- [6th generation Intel-based VMs – Dv6/Ev6 (Public Preview)](https://azure.microsoft.com/en-us/updates/v2/6th-generation-Intel-based-VMs-Dv6-Ev6) : General Purpose and Memory-optimised variants, initially available in US West and US East. [Claimed performance increase over v5 VMs as well as increased scalability](https://techcommunity.microsoft.com/t5/azure-compute-blog/announcing-preview-of-new-azure-dlsv6-dsv6-esv6-vms-with-new-cpu/ba-p/4192124). Also support [Azure Boost](https://learn.microsoft.com/en-gb/azure/azure-boost/overview) for increased performance (as will all new VM series going forward).

## Governance

- [Azure Essentials](https://azure.microsoft.com/en-us/solutions/azure-essentials) | [Azure Migrate and Modernize | Azure Innovate](https://azure.microsoft.com/en-us/solutions/migration/migrate-modernize-innovate) - Curated collections of resources to [kick off and develop Azure projects](https://techcommunity.microsoft.com/t5/azure-governance-and-management/mastering-your-cloud-journey-essentials-to-innovating-migrating/ba-p/4195533). Quite a heavy focus on AI (unsurprisingly :-) but covers other areas as well. Useful starting points to go with resources like the Well-Architected and Cloud Adoption Frameworks.