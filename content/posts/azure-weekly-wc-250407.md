+++
title = 'Azure Snippets w/c 07/04/2025 - AKS Edition'
date = 2025-04-07T20:00:16+01:00
draft = true
categories = ['Azure Weekly 2025']
tags = ['AKS']
+++

Summary of Azure snippets for the week commencing 7th April 2025. As so many AKS updates have dropped recently, I've decided to do a special AKS edition post to round them all up.

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

## Azure Kubernetes Services

- [AKS Release 2025-03-16 now available (GA)](https://github.com/Azure/AKS/releases/tag/2025-03-16) : Highlights include AKS 1.28 becoming the next LTS version, patch versions 1.29.12, 1.29.13, 1.30.8, 1.30.9, 1.31.4, and 1.31.5 now available, and a quota for AKS clusters in a subscription is being introduced

- [CNI Overlay for Application Gateway for Containers and AGIC (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=485357) : App Gateway for Containers and App Gateway Ingress Controller haven't supported CNI overlay networking to date, so this is welcome.

- [AKS Communication Manager (GA)](https://azure.microsoft.com/en-gb/updates?id=486498) : The [AKS communication manager](https://learn.microsoft.com/en-us/azure/aks/aks-communication-manager) streamlines notifications for all your AKS maintenance tasks by using Azure Resource Notification and Azure Resource Graph frameworks. This tool enables you to monitor your upgrades closely by providing timely alerts on event triggers and outcomes. Another preview feature transferring to GA quickly!

- [Azure CNI Overlay Dual-stack with Cilium Dataplane Support (GA)](https://azure.microsoft.com/en-gb/updates?id=486814) : Azure CNI overlay now supports [dual-stack networking with Azure CNI powered by Cilium](https://learn.microsoft.com/en-gb/azure/aks/azure-cni-overlay?tabs=kubectl#dual-stack-networking-with-azure-cni-powered-by-cilium), enabling customers to enforce IPv6 network policies and leverage [Advanced Container Networking Services (ACNS)](https://learn.microsoft.com/en-gb/azure/aks/advanced-container-networking-services-overview?tabs=cilium) in dual-stack environments.

- [Application Insights auto-instrumentation for AKS (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=486716) : To provide seamless monitoring for Java and Node deployments, AKS now offers Application Insights integration for Java and Node microservices. This integration, available in public preview, allows customers to easily monitor their deployments without changing any code by leveraging [auto-instrumentation](https://learn.microsoft.com/en-us/azure/azure-monitor/app/kubernetes-codeless) that is integrated into the AKS cluster.

- [Multi-cluster Auto-upgrade in Azure Kubernetes Fleet Manager (GA)](https://azure.microsoft.com/en-gb/updates?id=486731) : [Auto-upgrade support](https://learn.microsoft.com/en-gb/azure/kubernetes-fleet/update-automation?tabs=azure-portal) provides an automated trigger for update runs based on new Kubernetes or node image versions being published to Azure. Admins can create multiple auto-upgrade profiles for their fleet to capture combinations of Kubernetes and node image version updates.

- [Multi-cluster Workload Rollout Strategies and Runs with Azure Kubernetes Fleet Manager (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=486736) : Operators using Azure Kubernetes Fleet Manager’s Cluster Resource Placement for intelligent execution of multi-cluster workload placement can now define reusable staged rollout strategies using [ClusterStagedUpdateStrategy](https://learn.microsoft.com/en-gb/azure/kubernetes-fleet/concepts-rollout-strategy#staged-update-strategy-preview) custom resource.

 - [Cilium WireGuard Encryption Support in AKS (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=486746) : AKS supports WireGuard encryption in Advanced Container Networking Services + Cilium data plane clusters. This enables seamless node-to-node encryption for improved security.

 -  [AKS Support for Persistent Network Flow Logging for Advanced Container Networking Services (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=486756) : To enable better security auditing, performance analysis, and troubleshooting of network flows within your AKS clusters, AKS now supports persistent network flow logging with Advanced Container Networking Services' [Container Network Observability](https://learn.microsoft.com/en-us/azure/aks/container-network-observability-concepts?tabs=cilium) feature. This enhancement allows you to capture and retain detailed network traffic logs over time.

 - [Standard Load Balancer (SLB) Health Probe Redesign in AKS (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=486784) : AKS now offers improved load balancing for services using externalTrafficPolicy: Cluster. This enhancement enables the standard load balancer (SLB) to probe kube-proxy directly instead of backend applications. This new capability enhances reliability, reduces misconfigurations, and improves traffic routing.

 - [maxUnavailable Setting for Upgrades in AKS (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=486809) : AKS now supports setting a [maxUnavailable option](https://learn.microsoft.com/en-us/azure/aks/upgrade-aks-cluster?tabs=azure-cli#customize-unavailable-nodes-during-upgrade-preview) for upgrading nodepools to a newer version of both Kubernetes and node images. With maxUnavailable, you no longer need to use surge nodes to begin the upgrade process. AKS will instead simply cordon and drain existing nodes on the nodepool.

 - [Azure CNI Node Subnet + Cilium Support (GA)](https://azure.microsoft.com/en-gb/updates?id=486751) : AKS now supports the Cilium dataplane with Azure CNI Node Subnet. This enhancement allows you to leverage Cilium’s advanced networking capabilities while using Node Subnet IP allocation, maintaining your existing IP allocation strategies.

 - [Advanced Container Networking Services Cilium L7 Policies Support in AKS (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=486774) : AKS now supports Layer 7 (L7) network policies in Advanced Container Networking Services + Cilium clusters, enabling fine-grained control over application traffic. With L7 policies, customers can define security rules based on application-layer attributes, improving zero-trust security models within AKS.
