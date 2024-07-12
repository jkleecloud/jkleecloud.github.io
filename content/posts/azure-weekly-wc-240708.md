+++
title = 'Azure Snippets w/c 08/07/2024'
date = 2024-07-12T08:00:16+01:00
draft = false
categories = ['Azure Weekly 2024']
tags = ['Azure Load Balancer', 'FinOps', 'AKS', 'Azure Policy']
+++

After a couple of weeks off due to holidays and a general lack of updates from MS, we now return to our regularly scheduled programming :-)

Summary of Azure snippets for the week commencing 8th July 2024, grouped by Azure service. No Azure Monthly summary this month as there's [only one other post for June](../azure-weekly-wc-240617/).

GA = Generally Available  
Public/Private Preview = as stated :-)

Azure services with highlighted updates this week:

- [Azure Load Balancer](#azure-load-balancer)
- [Azure Kubernetes Service](#azure-kubernetes-service)
- [Azure Policy](#azure-policy)
- [FinOps](#finops)

## Azure Load Balancer

- [Cross-subscription load balancer (Public Preview)](https://techcommunity.microsoft.com/t5/azure-networking-blog/build-scalable-cross-subscription-applications-with-azure-load/ba-p/4167505) : Allows the frontend IP and/or the backend pool instances [to be in a different subscription from the Azure Load Balancer resource](https://learn.microsoft.com/en-us/azure/load-balancer/cross-subscription-overview). Useful if networking and application resources are split across subscriptions, for instance.

## Azure Kubernetes Service

- Some interesting items in the [latest AKS release](https://github.com/Azure/AKS/releases/tag/2024-06-27) : 
    - K8s 1.30 will be the next LTS version in AKS
    - AKS patch versions 1.27.14, 1.28.10, and 1.29.5, are now available. 1.27.9, 1.28.5, and 1.29.2 patch versions are deprecated.
    - [Cost Analysis](https://learn.microsoft.com/en-gb/azure/aks/cost-analysis) is now [available on AKS resource blades](https://learn.microsoft.com/en-gb/azure/cost-management-billing/costs/view-kubernetes-costs) (shows as Preview if enabled on your tenant). It's available for Standard and Premium tier clusters only and must be enabled (as an add-on) on every cluster you wish to view costs for.
- Copilot in Azure can now [assist with cluster management using kubectl](https://techcommunity.microsoft.com/t5/itops-talk-blog/microsoft-copilot-in-azure-series-kubectl/ba-p/4188499)

## Azure Policy
- [Built-in versioning (Public Preview)](https://techcommunity.microsoft.com/t5/azure-governance-and-management/public-preview-announcement-azure-policy-built-in-versioning/ba-p/4186105) : Policies (and initiatives) can now have multiple versions but keep a single definition ID for reference. Follows semantic versioning standard. Should be a boost to Policy governance and management.

## FinOps

- [FinOps toolkit](https://microsoft.github.io/finops-toolkit/) : The Microsoft FinOps toolkit is an open-source collection of learning resources and customizable tools to help you adopt and implement FinOps capabilities that automate and extend the Microsoft Cloud. There's a lot of stuff in here across Azure Monitor, Power BI, and tools and automations in PowerShell and Bicep. Aligned with the [FinOps Open Cost and Usage Specification (FOCUS)](https://focus.finops.org/) standard.
