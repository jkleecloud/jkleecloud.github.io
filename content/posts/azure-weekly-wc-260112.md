+++
title = 'Azure Snippets w/c 12/01/2026'
date = 2026-01-12T08:00:16Z
draft = false
categories = ['Azure Weekly 2026']
tags = ['AKS', 'Virtual Networks', 'Service Bus']
+++

Summary of Azure snippets for the week commencing 12th January 2026, grouped by Azure service.

Welcome to the first post of 2026! Bit of an unplanned hiatus due to busyness, then Christmas and New Year happened. Belated Happy New Year to my reader :-)

With it being the post-Christmas and New Year period, there hasn't been too much happening in the Azure space lately, but I have spotted a couple of interesting developments in the latest AKS release and with the Power Platform. Also, Ignite took place last November - here's links to the [Book of News](https://news.microsoft.com/ignite-2025-book-of-news/) and a [summary of updates in Azure](https://azure.microsoft.com/en-us/blog/azure-at-microsoft-ignite-2025-all-the-intelligent-cloud-news-explained/) since I didn't get a chance to post them earlier on.

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [Azure Kubernetes Services](#azure-kubernetes-services)
- [Service Bus](#service-bus)
- [Virtual Networks](#virtual-networks)

## Azure Kubernetes Services

- [AKS Release 2026-01-04 now available (GA)](https://github.com/Azure/AKS/releases/tag/2026-01-04) : Among the items in this release:
    - AKS Kubernetes v1.31 is now deprecated and v1.34 is now GA
    - LTS versions updated up to v1.30
    - [Latest results from the CIS Kubernetes security benchmark](https://learn.microsoft.com/en-gb/azure/aks/cis-kubernetes) against AKS
    - Several new preview features - I pull out a couple of these below, check the release documentation for the full list

- [Azure CNI Overlay networking support for Pod CIDR address space expansion (Public Preview)](https://learn.microsoft.com/en-gb/azure/aks/azure-cni-overlay-pod-expand) : Add more pod IP addresses without having to recreate the cluster

- [Istio CNI (Public Preview)](https://learn.microsoft.com/en-gb/azure/aks/istio-cni) : This [doesn't replace Azure CNI](https://learn.microsoft.com/en-gb/azure/aks/istio-cni#overview) for pod networking (so it isn't an alternative to [Cilium](https://learn.microsoft.com/en-gb/azure/aks/azure-cni-powered-by-cilium), for instance), but moves the Istio service mesh networking config for application workloads from privileged containers in pods to a cluster-level plugin.

- [Cloud-native apps on Kubernetes pricing calculator scenario (GA)](https://azure.microsoft.com/en-us/updates?id=536560) : The new cloud-native apps on Kubernetes pricing calculator scenario allows teams to estimate the total cost of ownership for a production-ready AKS cluster with other key Azure services, including Azure Container Registry, Azure Monitoring, Microsoft Defender for Cloud, and more. The calculator scenario provides an architecture diagram and cost estimate with customizable inputs to fit your workload requirements. This looks like it could be very useful, as cost estimations can be tricky for these scenarios - including an architecture diagram that can be used as a baseline is a nice touch as well.

## Service Bus

- [Geo-replication for Azure Service Bus Premium (GA)](https://azure.microsoft.com/en-us/updates?id=490149) : The [Service Bus Geo-Replication feature](https://learn.microsoft.com/en-gb/azure/service-bus-messaging/service-bus-geo-replication) is one of the options to [insulate Azure Service Bus applications against outages and disasters](https://learn.microsoft.com/en-gb/azure/service-bus-messaging/service-bus-outages-disasters), providing replication of both metadata (entities, configuration, properties) and data (message data and message property / state changes). The Geo-Replication feature ensures that the metadata and data of a namespace are continuously replicated from a primary region to one or more secondary regions. Moreover, it allows promoting any secondary region to primary, at any time.

## Virtual Networks

- [Cross-Region Zero Trust: Connecting Power Platform to Azure PaaS across different regions](https://techcommunity.microsoft.com/blog/azurearchitectureblog/cross-region-zero-trust-connecting-power-platform-to-azure-paas-across-different/4484995) : Describes how to set up a Cross-Region Private Link that routes traffic from a Power Platform implementation in Region A, through a secure Azure Hub, and down the Azure Global Backbone to a Private Endpoint in Region B, without a single packet ever touching the public internet.