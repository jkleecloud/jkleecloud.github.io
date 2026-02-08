+++
title = 'Azure Snippets w/c 02/02/2026'
date = 2026-02-09T08:00:16+01:00
draft = true
categories = ['Azure Weekly 2026']
tags = ['AKS', 'Azure Storage', 'IaC]
+++

Summary of Azure snippets for the week commencing 2nd February 2026, grouped by Azure service.

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [Azure Kubernetes Services](#azure-kubernetes-services)
- [Azure Storage](#azure-storage)
- [Infrastructure as Code](#infrastructure-as-code)

## Azure Kubernetes Services

- [Deployment safeguards – pod security standard support in AKS (GA)](https://azure.microsoft.com/en-us/updates?id=548101) : Azure Kubernetes Service (AKS) now supports Kubernetes [Pod Security Standards](https://kubernetes.io/docs/concepts/security/pod-security-standards/) within [Deployment Safeguards](https://learn.microsoft.com/en-gb/azure/aks/deployment-safeguards#pod-security-standards-error-messages), enabling centralized management of Baseline, Restricted, and Privileged standards at scale. This capability allows teams to ensure that deployment manifests comply with selected security standards, help technical practitioners strengthen workload security, reduce configuration drift, and simplify the rollout of cluster-wide security controls.

- [Retina 1.0 Is Now Available (GA)](https://techcommunity.microsoft.com/blog/linuxandopensourceblog/retina-1-0-is-now-available/4489003) : Retina is an open-source, Kubernetes network observability platform. It enables you to continuously observe and measure network health, and investigate network issues on-demand with integrated Kubernetes-native workflows. (I've put this in the AKS section, but there are no Azure dependencies - Retina runs anywhere Kubernetes does and can be used across distributions.)

## Azure Storage

- [User delegation SAS for Azure Tables, Azure Files, and Azure Queues (Public Preview)](https://azure.microsoft.com/en-us/updates?id=548987) : [User delegation SAS](https://learn.microsoft.com/en-gb/rest/api/storageservices/create-user-delegation-sas) for Azure Tables, Azure Files, and Azure Queues is now available in public preview. User delegation (UDK) SAS is already generally available for blobs, and this release extends that support to tables, files, and queues. User delegation SAS allows users to create a more secure SAS token than account or service SAS by tying the SAS token to the delegator.

## Infrastructure as Code

- [Release of Bicep Azure Verified Modules for Platform Landing Zone (GA)](https://techcommunity.microsoft.com/blog/azuretoolsblog/release-of-bicep-azure-verified-modules-for-platform-landing-zone/4487932) : Azure Verified Modules (AVM) represent Microsoft's unified approach to Infrastructure as Code. Born from the need to eliminate fragmentation across Microsoft's infrastructure-as-code (IaC) ecosystem, AVM provides consistent module standards, rigorous testing frameworks, and clear contribution guidelines. This release represents a significant milestone in the evolution of Azure Landing Zones. Bicep customers can now leverage the same modular, flexible, and battle-tested approach that our Terraform community has been using, all built on the foundation of Azure Verified Modules.

