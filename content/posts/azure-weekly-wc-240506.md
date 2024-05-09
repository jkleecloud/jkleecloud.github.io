+++
title = 'Azure Snippets w/c 06/05/2024'
date = 2024-05-07T11:54:50+01:00
draft = false
categories = ['Azure Weekly']
tags = ['API Center', 'Virtual Network Manager', 'Defender for Cloud', 'DB for PostgreSQL', 'Resource Graph', 'Change Analysis', 'Virtual Networks', 'Cloud Services (classic)', 'Virtual Network Encryption', 'Private Link', 'Azure Storage Actions', 'Azure Storage', 'AKS']
+++

Summary of Azure snippets for the week commencing 6th May 2024, grouped by Azure service.

GA = Generally Available  
Public/Private Preview = as stated :-)

Azure services with highlighted updates this week:

- [API Center](#api-center)
- [Azure DB for PostgreSQL](#azure-db-for-postgresql)
- [Azure Kubernetes Service](#azure-kubernetes-service)
- [Azure Resource Graph](#azure-resource-graph)
- [Azure Storage](#azure-storage)
- [Cloud Services (classic)](#cloud-services-classic)
- [Defender for Cloud](#defender-for-cloud)
- [Virtual Network Manager](#virtual-network-manager)
- [Virtual Networks](#virtual-networks)

## API Center

- [API Center (GA)](https://azure.microsoft.com/en-gb/updates/general-availability-azure-api-center/) : A centralised solution for delivery, consumption and governance of APIs. Provides (among other features): cataloguing and inventory of APIs (including from APIM), governance and design rule enforcement, API Analysis for consistency and compliance, and a Visual Studio Code extension for an enhanced developer experience. More full featured than I thought - is this the future of the APIM developer portal?
    - [Azure API Center GA blog post](https://techcommunity.microsoft.com/t5/azure-integration-services-blog/azure-api-center-your-comprehensive-api-inventory-and-governance/ba-p/4125146)

## Azure DB for PostgreSQL

- [Azure Database for PostgreSQL - Flexible Server enhanced disaster recovery features (GA)](https://azure.microsoft.com/en-gb/updates/general-availability-azure-database-for-postgresql-flexible-server-enhanced-disaster-recovery-features/) : Enhancements to the read replicas feature - Virtual Endpoints and promote a read replica to primary server
    - [Virtual endpoints for read replicas](https://learn.microsoft.com/en-gb/azure/postgresql/flexible-server/concepts-read-replicas-virtual-endpoints)
    - [Promote to primary server](https://learn.microsoft.com/en-gb/azure/postgresql/flexible-server/concepts-read-replicas-promote)
- [Azure Database for PostgreSQL - Flexible Server networking with Azure Private Link (GA)](https://azure.microsoft.com/en-gb/updates/general-availability-azure-database-for-postgresql-flexible-server-networking-with-azure-private-link/) : Private Link joins VNet integration as a supported private VNet access method for PostgreSQL Flexible Server
    - [Networking with Private Endpoint docs](https://learn.microsoft.com/en-gb/azure/postgresql/flexible-server/concepts-networking-private-link)

## Azure Kubernetes Service

- [Initialization taints (Public Preview)](https://azure.microsoft.com/en-gb/updates/public-preview-initialization-taints-in-aks/) : Temporary taints on AKS nodes, for example if more time is needed to set up nodes
    - [Node initialisation taints docs](https://learn.microsoft.com/en-gb/azure/aks/use-node-taints#use-node-initialization-taints-preview)

## Azure Resource Graph

- [Azure Change Analysis - New Portal experience (Public Preview)](https://azure.microsoft.com/en-gb/updates/public-preview-azure-change-analysis-new-portal-experience/) : See all resoure changes across all tenants and subscriptions in the Azure Portal. New portal experience includes filtering, grouping and [Change Actor](https://azure.microsoft.com/en-us/updates/public-preview-change-actor/) (who made the change and how)
    - [View resource changes in the Azure portal (Learn)](https://learn.microsoft.com/en-us/azure/governance/resource-graph/changes/view-resource-changes)
    - [Change Actor (public preview)](https://azure.microsoft.com/en-us/updates/public-preview-change-actor/)

## Azure Storage
- [Azure Storage Actions (public preview)](https://azure.microsoft.com/en-gb/updates/public-preview-azure-storage-actions-is-now-available-in-14-more-regions/) : Serverless and no-code framework for managing storage operations. Currently supports operations on Blobs in Storage Accounts, and isn't available in UK regions yet.
- [SLA on Blob Storage Cold Tier (GA)](https://azure.microsoft.com/en-gb/updates/generally-available-service-level-agreement-on-azure-blob-storage-cold-tier/) : Cold tier Blob storage now backed with a Microsoft uptime and connectivity SLA.

## Cloud Services (classic)

- [Cloud Services (classic) deployment model is retiring on 31 August 2024](https://azure.microsoft.com/en-gb/updates/cloud-services-classic-retirement-announcement-apr2024/) : Migrate to Cloud Services (extended support) if you need to keep using them
    - [Five classic networking services](https://azure.microsoft.com/en-gb/updates/classic-networking-retirements-april2024/) which depend on classic Cloud Services are also being retired

## Defender for Cloud

- [Azure Defender for Microsoft Azure Database for PostgreSQL - Flexible Server (GA)](https://azure.microsoft.com/en-gb/updates/general-availability-azure-defender-for-microsoft-azure-database-for-postgresql-flexible-server/) : Part of the [Defender for open-source relational databases plan](https://learn.microsoft.com/en-gb/azure/defender-for-cloud/defender-for-databases-introduction) which includes MySQL and MariaDB as well. I have no idea why they refer to it as Azure Defender (the old name for Microsoft Defender for Cloud) here!
    - [Azure DB for PostgreSQL docs - Defender for Cloud support](https://learn.microsoft.com/en-gb/azure/postgresql/flexible-server/concepts-security#microsoft-defender-for-cloud-support)

## Virtual Network Manager

- [Virtual Network Manager UDR (Public Preview)](https://azure.microsoft.com/en-gb/updates/azure-virtual-network-manager-userdefined-route-udr-management-now-in-public-preview/) : Enabling users to describe their desired routing behavior via configuration, simplifying the management of routing behaviors at scale.
- [Azure Virtual Network Manager security admin rule (GA)](https://azure.microsoft.com/en-gb/updates/azure-virtual-network-manager-security-admin-rule-generally-available-in-all-public-regions/) : Empowering users to enforce security rules across their virtual networks globally.
    - [Security admin rule concepts](https://learn.microsoft.com/en-us/azure/virtual-network-manager/concept-security-admins)

## Virtual Networks

- [Virtual network flow logs (GA)](https://azure.microsoft.com/en-gb/updates/general-availability-virtual-network-flow-logs/) : New capability of Network Watcher, enhancing the flow log support already available for NSGs to the VNet scope
    - [Azure Networking blog announcement](https://techcommunity.microsoft.com/t5/azure-networking-blog/network-traffic-observability-with-virtual-network-flow-logs/ba-p/4112907)
    - [VNet flow logs](https://learn.microsoft.com/en-us/azure/network-watcher/vnet-flow-logs-overview)
 - [Virtual Network encryption in all regions (GA)](https://azure.microsoft.com/en-gb/updates/general-availability-azure-virtual-network-encryption-availability-in-all-regions/) :  Customers can enable encryption of traffic between Virtual Machines and Virtual Machines Scale Sets within the same virtual network and between regionally and globally peered virtual networks. This new feature enhances the existing encryption in transit capabilities in Azure.
    - [Virtual Network encryption docs](https://azure.microsoft.com/en-gb/updates/general-availability-azure-virtual-network-encryption-availability-in-all-regions/)