+++
title = 'Azure Snippets w/c 02/02/2026'
date = 2026-02-09T08:00:16+01:00
draft = false
categories = ['Azure Weekly 2026']
tags = ['AKS', 'Azure Storage', 'IaC', 'Azure Backup', 'Compute', 'Virtual Networks']
+++

Summary of Azure snippets for the week commencing 2nd February 2026, grouped by Azure service.

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [Azure Backup](#azure-backup)
- [Azure Kubernetes Services](#azure-kubernetes-services)
- [Azure Storage](#azure-storage)
- [Compute](#compute)
- [Infrastructure as Code](#infrastructure-as-code)
- [Virtual Networks](#virtual-networks)

## Azure Backup

- [Vaulted Backups for Azure Disk (Private Preview)](https://azure.microsoft.com/en-us/updates?id=555184) : Disk backup finally gets a Vaulted tier along with the current Operational tier. The private preview introduces this along with regional disaster recovery to allow disk backups to be restored to a paired region.

## Azure Kubernetes Services

- [Deployment safeguards – pod security standard support in AKS (GA)](https://azure.microsoft.com/en-us/updates?id=548101) : Azure Kubernetes Service (AKS) now supports Kubernetes [Pod Security Standards](https://kubernetes.io/docs/concepts/security/pod-security-standards/) within [Deployment Safeguards](https://learn.microsoft.com/en-gb/azure/aks/deployment-safeguards#pod-security-standards-error-messages), enabling centralized management of Baseline, Restricted, and Privileged standards at scale. This capability allows teams to ensure that deployment manifests comply with selected security standards, help technical practitioners strengthen workload security, reduce configuration drift, and simplify the rollout of cluster-wide security controls.

- [Retina 1.0 Is Now Available (GA)](https://techcommunity.microsoft.com/blog/linuxandopensourceblog/retina-1-0-is-now-available/4489003) : Retina is an open-source, Kubernetes network observability platform. It enables you to continuously observe and measure network health, and investigate network issues on-demand with integrated Kubernetes-native workflows. (I've put this in the AKS section, but there are no Azure dependencies - Retina runs anywhere Kubernetes does and can be used across distributions.)

## Azure Storage

- [User delegation SAS for Azure Tables, Azure Files, and Azure Queues (Public Preview)](https://azure.microsoft.com/en-us/updates?id=548987) : [User delegation SAS](https://learn.microsoft.com/en-gb/rest/api/storageservices/create-user-delegation-sas) for Azure Tables, Azure Files, and Azure Queues is now available in public preview. User delegation (UDK) SAS is already generally available for blobs, and this release extends that support to tables, files, and queues. User delegation SAS allows users to create a more secure SAS token than account or service SAS by tying the SAS token to the delegator.

## Compute

- [7th generation Intel-based VMs – Dlsv7/Dsv7/Esv7 (Public Preview)](https://azure.microsoft.com/en-us/updates?id=529407) : A year after the [6th generation](https://jkleecloud.github.io/posts/azure-weekly-wc-250210/) General Purpose and Memory Optimised VMs went GA, the 7th generation is now in preview. Powered by the latest Intel® Xeon® 6 processors (Granite Rapids), the latest Azure Intel-based v7 VMs are designed to power ever increasing compute demands in today’s data center environment and deliver exceptional performance across a wide range of workloads, from traditional enterprise applications to cutting edge AI. Among other improvements, these VMs can scale up to 372 vCPUs with Esv7 VMs enabling up to 2.8TiB of memory. (7th generation [AMD-based VMs are already GA](https://techcommunity.microsoft.com/blog/azurecompute/announcing-general-availability-of-azure-daeafasv7-series-vms-based-on-amd-%E2%80%98turi/4488627) - available in UK South but not UK West yet.)

## Infrastructure as Code

- [Release of Bicep Azure Verified Modules for Platform Landing Zone (GA)](https://techcommunity.microsoft.com/blog/azuretoolsblog/release-of-bicep-azure-verified-modules-for-platform-landing-zone/4487932) : Azure Verified Modules (AVM) represent Microsoft's unified approach to Infrastructure as Code. Born from the need to eliminate fragmentation across Microsoft's infrastructure-as-code (IaC) ecosystem, AVM provides consistent module standards, rigorous testing frameworks, and clear contribution guidelines. This release represents a significant milestone in the evolution of Azure Landing Zones. Bicep customers can now leverage the same modular, flexible, and battle-tested approach that our Terraform community has been using, all built on the foundation of Azure Verified Modules.

## Virtual Networks

- [Azure virtual network routing appliance (Public Preview)](https://azure.microsoft.com/en-us/updates?id=555944) : The virtual network routing appliance is an Azure-managed network routing device that you deploy inside your virtual network. It acts as a high-bandwidth forwarding layer for routed traffic flows, so you don't need to run your own virtual machines as the forwarding layer. It's deployed into a dedicated subnet, where it acts as a managed forwarding router. Traffic can be routed using User Defined Routes (UDR) enabling spoke to spoke communication in traditional Hub & Spoke topologies. A fully Azure-native routing appliance, deployed as an ARM resource, could be an interesting option for hub-and-spoke topologies. UK South is one of the preview regions.

