+++
title = 'Azure Snippets w/c 11/08/2025'
date = 2025-08-13T08:00:16+01:00
draft = true
categories = ['Azure Weekly 2025']
tags = ['Application Gateway', 'AKS', 'Azure Storage', 'Network Security Perimeter', 'Virtual Network Manager', 'Azure Monitor']
+++

Summary of Azure snippets for the week commencing 11th August 2025, grouped by Azure service. Lots of AKS announcements this time, but there are a few other service updates as well (including one that I've personally been waiting a while for!).

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [Application Gateway](#application-gateway)
- [Azure Kubernetes Services](#azure-kubernetes-services)
- [Azure Monitor](#azure-monitor)
- [Azure Storage](#azure-storage)
- [Network Security Perimeter](#network-security-perimeter)
- [Virtual Network Manager](#virtual-network-manager)

## Application Gateway

- [Private Application Gateway on Application Gateway v2 (GA)](https://azure.microsoft.com/en-us/updates?id=500225) : I've been waiting for this feature to go GA for more than 2 years now! Finally, [private deployments for the v2 Application Gateway](https://learn.microsoft.com/en-us/azure/application-gateway/application-gateway-private-deployment?tabs=portal) are available. These permit: private IP only frontend configuration (no Public IP address is required for management); enhanced control over Network Security Groups (the GatewayManager inbound rules are no longer needed and you can define a 'Deny All' outbound rule to drop other traffic); and enhanced UDR support (forced tunnelling to a network appliance using the '0.0.0.0/0' rule is now supported).

## Azure Kubernetes Services

- [Deployment safeguards (GA)](https://azure.microsoft.com/en-us/updates?id=499299) : [Deployment Safeguards](https://learn.microsoft.com/en-gb/azure/aks/deployment-safeguards) enforce Kubernetes best practices in your AKS cluster through Azure Policy controls. This looks to be an Azure Policy initiative containing AKS-specific best practice policies, that can be enabled as a set through Deployment Safeguards. Azure Policy add-on is required in your AKS cluster to use them.

- [AKS Model Context Protocol (MCP) server (Public Preview)](https://azure.microsoft.com/en-us/updates?id=499326) : Model Context Protocol (MCP) server for AKS is now available as an [open source release](https://github.com/Azure/aks-mcp). This foundational component enables AI agents to interact with AKS clusters and simplifies cluster management. Get building your AKS cluster AI management tools!

- [Agentic experience for AKS in the Azure CLI (Private Preview)](https://azure.microsoft.com/en-us/updates?id=499377) : Second AKS AI angle of the post! The Azure Kubernetes Service (AKS) team is introducing a new agentic AI-powered CLI experience through the “az aks agent” command. This feature brings the intelligence of agentic reasoning directly into the Azure CLI, enabling developers and operators to interact with their clusters using natural language powered by agentic AI. Limited preview with signup - not much more information about it just now.

- [Azure Bastion integration with AKS (Public Preview)](https://azure.microsoft.com/en-us/updates?id=499335) : This integration enables continuous secure access to private AKS clusters and also applies to AKS public clusters with API server authorised IP ranges. Users can now connect to their clusters and easily use native Kubernetes tooling (e.g. kubectl) from their local machines, using [Bastion's native client tunneling feature](https://learn.microsoft.com/en-us/azure/bastion/bastion-connect-to-aks-private-cluster). Bastion must be Premium or Standard SKU (so it won't work with Developer at present).

- [LocalDNS for AKS (Public Preview)](https://azure.microsoft.com/en-us/updates?id=499341) : With [LocalDNS](https://learn.microsoft.com/en-us/azure/aks/dns-concepts#localdns-in-azure-kubernetes-service-preview), a DNS proxy is deployed on each node, which enables faster, more reliable DNS resolution. LocalDNS delivers instant performance gains without application level changes, plus [advanced DNS customization](https://learn.microsoft.com/en-us/azure/aks/localdns-custom) for both internal and external domains.

- [Static egress gateway public prefix support in AKS (GA)](https://azure.microsoft.com/en-us/updates?id=499351) : This feature allows AKS customers to create a dedicated gateway node pool that routes outbound traffic from annotated pods through a static public IP prefix (/28 to /31). It enables customers to achieve consistent and predictable egress IPs for firewall whitelisting, compliance, and partner integration scenarios. Note that the [static egress gateway](https://learn.microsoft.com/en-gb/azure/aks/configure-static-egress-gateway) doesn't work with Private IPs - it must have a public IP prefix (a range of contiguous public IP addresses) assigned.

- [Multiple Standard Load Balancers support in AKS (Public Preview)](https://azure.microsoft.com/en-us/updates?id=499356) : AKS normally provisions one Standard Load Balancer (SLB) for all LoadBalancer Services in a cluster. Because each node NIC is limited to 300 inbound load‑balancing rules and 8 private‑link services, large clusters or port‑heavy workloads can quickly exhaust these limits. The [multiple SLB preview](https://learn.microsoft.com/en-gb/azure/aks/use-multiple-standard-load-balancer) removes that bottleneck by letting you create several SLBs inside the same cluster and shard nodes and Services across them. You can also isolate traffic by assigning different SLBs to different agent pools and workloads, with AKS managing the node and Service placements.

- [Azure Virtual Network Verifier (VNV) for AKS (Public Preview)](https://azure.microsoft.com/en-us/updates?id=499361) : [Azure Virtual Network Verifier for AKS](https://learn.microsoft.com/en-gb/troubleshoot/azure/azure-kubernetes/connectivity/basic-troubleshooting-outbound-connections#check-if-azure-network-resources-are-blocking-traffic-to-the-endpoint) (seemingly also known as [Connectivity Analysis](https://techcommunity.microsoft.com/blog/appsonazureblog/simplifying-outbound-connectivity-troubleshooting-in-aks-with-connectivity-analy/4441200) and using the VNV functionality in Virtual Network Manager) is a tool which allows you to detect and troubleshoot outbound connectivity issues in your AKS cluster. You can use the Virtual Network Verifier feature to run a connectivity analysis to check the traffic flow between your cluster and a public egress endpoint. Note that full region support for CNI Overlay clusters is currently being rolled out.

- [AKS Security Dashboard (GA)](https://azure.microsoft.com/en-us/updates?id=499366) : The [AKS Security Dashboard](https://learn.microsoft.com/en-us/azure/defender-for-cloud/cluster-security-dashboard) provides a centralized view of security posture and runtime threat protection for your AKS cluster within the Azure Portal. It highlights software vulnerabilities, critical security issues, compliance gaps, and active threats, helping you prioritize remediation. A way of showing the information from Defender for Containers and/or DCSPM from in a dashboard AKS-side, rather than having to go into Defender for Cloud.

- [Managed Namespaces in AKS (Public Preview)](https://azure.microsoft.com/en-us/updates?id=499371) : [Managed namespaces](https://learn.microsoft.com/en-gb/azure/aks/concepts-managed-namespaces) for AKS allows users to get a list of namespaces they have access to across a subscription, resource group, and cluster, and then retrieve credentials that will give them the ability to deploy to those [namespaces](https://learn.microsoft.com/en-gb/azure/aks/managed-namespaces?pivots=azure-portal).

## Azure Monitor

- [Tenant-Level Service Health Alerts (Public Preview)](https://azure.microsoft.com/en-us/updates?id=499776) : Enables customers to receive proactive notifications about service health issues impacting their entire tenant, not just individual subscriptions. With this feature, you can now [create alert rules scoped at the directory (tenant) level](https://learn.microsoft.com/en-gb/azure/azure-monitor/alerts/alerts-create-tenant-level-service-heath-alerts) directly from the Service Health page or the alert rule creation wizard in the Azure portal. 

## Azure Storage

- [Azure Storage Discovery (Public Preview)](https://azure.microsoft.com/en-us/updates?id=499143) : [Azure Storage Discovery](https://learn.microsoft.com/en-gb/azure/storage-discovery/overview) is a fully managed service that provides enterprise-wide visibility into your Azure Blob Storage data estate. In a single pane of glass you can understand and analyze how your data estate evolved over time, optimize costs, enhance security, and drive operational efficiency. Azure Storage Discovery integrates with Copilot in Azure, enabling you to unlock insights and accelerate decision-making without utilizing any query language. Interesting service - another edition to the 'enterprise management' Azure services like API Center, and potentially very useful for getting to grips with a large Azure storage estate (Blobs, anyway, since that's the only storage service supported at this stage). [Free and Standard tiers](https://learn.microsoft.com/en-gb/azure/storage-discovery/pricing) are available.

## Network Security Perimeter

- [Network Security Perimeter (GA)](https://azure.microsoft.com/en-us/updates?id=496002) : [Network security perimeter](https://learn.microsoft.com/en-us/azure/private-link/network-security-perimeter-concepts) allows organizations to define a logical network isolation boundary for PaaS resources (for example, Azure Storage account and SQL Database server) that are deployed outside your organization’s virtual networks. It restricts public network access to PaaS resources within the perimeter; access can be exempted by using explicit access rules for public inbound and outbound. Announced in preview in December 2024. Now part of the networking config for supported resource at configuration time if you go through the wizard in the portal (e.g. Storage Accounts) - looks like Microsoft are positioning it as the 'next iteration' of Private Link and as the 'most secure' option for PaaS service networking (since the perimeter controls both inbound and outbound access to the service in question).

## Virtual Network Manager

- [Azure Virtual Network Manager mesh connectivity (Public Preview)](https://azure.microsoft.com/en-us/updates?id=499782) : [Azure Virtual Network Manager](https://learn.microsoft.com/en-us/azure/virtual-network-manager/overview) mesh connectivity is now in public preview, enabling you to group up to 5,000 virtual networks in supported regions.


