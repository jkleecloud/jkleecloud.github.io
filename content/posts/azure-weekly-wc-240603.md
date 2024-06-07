+++
title = 'Azure Snippets w/c 03/06/2024'
date = 2024-06-07T08:00:16+01:00
draft = false
categories = ['Azure Weekly 2024']
tags = ['Azure Load Balancer', 'APIM', 'Azure Monitor', 'Azure Bastion', 'Compute']
+++

Summary of Azure snippets for the week commencing 3rd June 2024, grouped by Azure service.

GA = Generally Available  
Public/Private Preview = as stated :-)

Azure services with highlighted updates this week:

- [API Management](#api-management)
- [Azure Bastion](#azure-bastion)
- [Azure Load Balancer](#azure-load-balancer)
- [Azure Monitor](#azure-monitor)
- [Compute](#compute)

## API Management

- [Audit logging in Developer portal (GA)](https://azure.microsoft.com/en-gb/updates/general-availability-audit-logging-in-azure-api-management-developer-portal/) : Audits user actions in the developer portal. Logs can be sent to a storage account, event hub or Log Analytics workspace (common pattern with diagnostic logs in Azure).

## Azure Bastion
- [Premium SKU (Public Preview)](https://azure.microsoft.com/en-gb/updates/public-preview-azure-bastion-premium/) : Adds session recording and private-only deployment to the [Standard SKU feature set](https://learn.microsoft.com/en-gb/azure/bastion/configuration-settings#skus). [Private-only deployment](https://learn.microsoft.com/en-gb/azure/bastion/private-only-deployment) is probably the major new feature here at the moment, though more features are apparently planned for Premium.

## Azure Load Balancer

- [Health Event Logs (Public Preview)](https://azure.microsoft.com/en-gb/updates/public-preview-azure-load-balancer-health-event-logs/) : I can think of several instances when this would have been useful :-) Health event logging through Azure Monitor to help troubleshoot ALB issues. [Supported for Standard (regional and global) and Gateway load balancers](https://learn.microsoft.com/en-us/azure/load-balancer/load-balancer-health-event-logs). A [good augmentation to the availability metrics](https://techcommunity.microsoft.com/t5/azure-networking-blog/introducing-azure-load-balancer-health-event-logs/ba-p/4154362) to get more detail - can be queried through Log Analytics and stored/parsed for historical data. UK South only for the preview.
- [Admin State (Public Preview)](https://azure.microsoft.com/en-gb/updates/public-preview-azure-load-balancer-now-supports-admin-state/) : Override a Load Balancer’s health probe behaviour for each individual backend pool instance without making changes to network security rules or closing ports on a VM. 'Maintenance mode' for ALBs (or for the backends) essentially - no need now to modify NSGs or VM config to block connections when maintaining the backends. Only works when a health probe is configured. [Documentation](https://learn.microsoft.com/en-gb/azure/load-balancer/admin-state-overview) and [blog post](https://techcommunity.microsoft.com/t5/azure-networking-blog/using-admin-state-to-control-your-azure-load-balancer-backend/ba-p/4155457) give more details on how it works. Preview available in all regions.

## Azure Monitor

- [Log Analytics Simple Mode (Public Preview)](https://azure.microsoft.com/en-gb/updates/public-preview-analyze-data-using-log-analytics-simple-mode/) : Point-and-click analysis of logs without having to know KQL - very useful! KQL mode still available for full-featured querying and analysis. [Part of the 'new' Log Analytics experience](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/log-analytics-simple-mode).
- [Kubernetes Metadata and Logs Filtering in Azure Monitor - Container Insights (Public Preview)](https://azure.microsoft.com/en-gb/updates/kubernetesmetadataandlogsfilteringpublicpreview/) : Enhances the ContainerLogsV2 schema with additional Kubernetes metadata. The Logs Filtering feature provides filtering capabilities for both workload and platform (i.e. system namespaces) logs coming out of containers. Visualise results with a [Grafana dashboard](https://grafana.com/grafana/dashboards/20995-azure-monitor-container-insights-containerlogv2/).
    - [Blog post](https://techcommunity.microsoft.com/t5/azure-observability-blog/announcing-public-preview-kubernetes-metadata-amp-logs-filtering/ba-p/4144654)
    - [Documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/containers/container-insights-logs-schema#kubernetes-metadata-and-logs-filtering)

## Compute

- [VM Hibernation (GA)](https://azure.microsoft.com/en-gb/updates/general-availability-vm-hibernation-general-purpose/) : Hibernation allows saving on compute costs, but persists the VM's in-memory state so apps etc. resume where they were left off (just like a physical machine hibernating). Available in all public regions.
    - [Documentation](https://learn.microsoft.com/en-us/azure/virtual-machines/hibernate-resume)
    - [Blog post](https://techcommunity.microsoft.com/t5/azure-compute-blog/cost-optimization-for-general-purpose-vms-using-hibernation-now/ba-p/4153399)
