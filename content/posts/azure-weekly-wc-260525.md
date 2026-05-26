+++
title = 'Azure Snippets w/c 25/05/2026'
date = 2026-05-26T08:00:16+01:00
draft = false
categories = ['Azure Weekly 2026']
tags = ['AI Foundry', 'Azure Backup', 'AKS', 'Azure Monitor', 'Azure Storage', 'Compute', 'Virtual Network Manager', 'Virtual Networks']
+++

Summary of Azure snippets for the week commencing 25th May 2026, grouped by Azure service.

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [AI Foundry](#ai-foundry)
- [Azure Backup](#azure-backup)
- [Azure Kubernetes Services](#azure-kubernetes-services)
- [Azure Monitor](#azure-monitor)
- [Azure Storage](#azure-storage)
- [Compute](#compute)
- [Virtual Network Manager](#virtual-network-manager)
- [Virtual Networks](#virtual-networks)

## AI Foundry

- [Microsoft Agent Framework 1.0 (GA)](https://azure.microsoft.com/en-us/updates?id=560982) : Microsoft Agent Framework is now at version 1.0 for both [.NET](https://www.nuget.org/packages/Microsoft.Agents.AI/) and [Python](https://pypi.org/project/agent-framework/), with stable APIs and a long-term support commitment. Agent Framework 1.0 supports multi-agent orchestration, multi-provider model support, and cross-runtime interoperability via A2A and MCP.

## Azure Backup

- [Bulk Restore for Azure Virtual Machines using Azure Backup (Public Preview)](https://azure.microsoft.com/en-us/updates?id=561373) : Enables customers to [restore multiple VMs](https://learn.microsoft.com/en-us/azure/backup/backup-azure-arm-restore-vms#restore-vms-in-bulk-preview) (up to 100) in a single operation. During large-scale outages or ransomware incidents, you can use bulk VM restore to orchestrate restore of multiple VMs as one coordinated operation that simplifies recovery at-scale. Each VM restore runs separately, and you can track its progress independently while retaining full VM-level flexibility and control.

## Azure Kubernetes Services

- [AKS Release 2026-04-28 now available (GA)](https://github.com/Azure/AKS/releases/tag/2026-04-28) : The main item to call out in this release is a mitigation for the Linux privilege escalation vulnerabilities referred to as Copy Fail, DirtyFrag and Fragnesia, which can allow an unprivileged pod to escalate to root on the underlying node. Make sure your node pools are updated - check the [AKS security bulletin](https://learn.microsoft.com/en-gb/azure/aks/security-bulletins/overview?tabs=aks-addons%2Caks-node-image%2Caks-cluster#aks-2026-0003-aks-advisory--mitigation-guide-for-cve-2026-31431-copy-fail) and the [advisory and mitigation guide](https://github.com/Azure/AKS/issues/5753). There are a number of other updates as well - check out the release notes for details.

- [Monitor AKS applications with OpenTelemetry and Azure Monitor (Public Preview)](https://azure.microsoft.com/en-us/updates?id=560119) : Azure Monitor now supports [monitoring applications that run on Azure Kubernetes Service (AKS) by using OpenTelemetry](https://learn.microsoft.com/en-gb/azure/azure-monitor/containers/kubernetes-open-protocol) for instrumentation and data collection. Leverage autoinstrumentation to deploy the Azure Monitor OpenTelemetry distro to workloads or use autoconfiguration to route OTLP signals from applications already instrumented with open-source, vendor neutral OpenTelemetry SDKs to Azure Monitor. A further move towards integrating OpenTelemetry with Azure Monitor - see also the section below.

- [Container Network Insights Agent (Public Preview)](https://azure.microsoft.com/en-us/updates?id=561020) : The [Container Network Insights Agent](https://learn.microsoft.com/en-us/azure/aks/container-network-insights-agent-overview) provides a lightweight, web‑based interface that translates natural‑language problem descriptions into read‑only diagnostics using live AKS cluster telemetry. It orchestrates safe diagnostic workflows and consolidates networking insights into structured summaries with recommended next steps. A Copilot for Kubernetes networking issues, essentially :-)

- [Observability in AKS Namespace and Workload Views (GA)](https://azure.microsoft.com/en-us/updates?id=560039) : AKS now surfaces observability data powered by Azure Monitor managed service for Prometheus directly within Namespace and Workload views in the Azure portal. With these enhanced insights, you can diagnose issues faster and gain a clearer understanding of cluster performance and resource usage.

 - [Application Insights Auto-instrumentation for Azure Kubernetes Service apps (GA)](https://azure.microsoft.com/en-gb/updates?id=562049) : [Azure Monitor Application Insights auto-instrumentation](https://learn.microsoft.com/en-gb/azure/azure-monitor/containers/kubernetes-codeless?tabs=portal) for Azure Kubernetes Service (AKS) apps makes it easier to monitor your applications without modifying source code. With just a few configuration steps, you can automatically instrument Java and Node.js workloads running on AKS and start collecting telemetry with Application Insights. Linux node pools only; [Python and .NET are in limited preview](https://learn.microsoft.com/en-gb/azure/azure-monitor/containers/kubernetes-codeless-python-net).

 - [Configure AKS backup using a single Azure CLI command (GA)](https://azure.microsoft.com/en-us/updates?id=560521) : Azure Backup now provides a simplified experience to [configure backup for AKS clusters using a single Azure CLI command](https://learn.microsoft.com/en-us/azure/backup/azure-kubernetes-service-cluster-backup-using-cli#configure-backup-using-a-single-azure-cli-command). Configuring Azure Backup for AKS has to date been something of a faff, requiring multiple steps to set up. The new command can perform all of these steps, and can optionally take a backup configuration file to use existing backup vaults, policies, or storage accounts during configuration.

## Azure Monitor

- [Azure Monitor dashboards with Grafana (GA)](https://azure.microsoft.com/en-us/updates?id=561564) : [Azure Monitor dashboards with Grafana](https://learn.microsoft.com/en-gb/azure/azure-monitor/visualize/visualize-use-grafana-dashboards) are generally available, bringing the power of Grafana’s open and composable visualization platform directly into the Azure Portal. With general availability, Azure Monitor dashboards with Grafana introduces new capabilities including expanded Azure service integrations (such as AKS, Application Insights and PostgreSQL), additional prebuilt dashboards, and support for advanced workflows like Grafana Explore and enhanced Kubernetes monitoring. This release is now broadly available across Azure clouds, including Azure Public, US Government (Fairfax), and China.

- [Support for native OTLP ingestion using the Azure Monitor Agent (Public Preview)](https://azure.microsoft.com/en-us/updates?id=560530) : Azure Monitor now supports [native ingestion of OpenTelemetry Protocol (OTLP) signals](https://learn.microsoft.com/en-gb/azure/azure-monitor/containers/opentelemetry-ingest-agent). Send telemetry directly from OpenTelemetry-instrumented applications by using the Azure Monitor Agent (AMA) to receive OTLP from your apps and export it to Azure Monitor. This is supported on Azure VMs, VM scale sets, and Azure Arc-enabled platforms (and also in AKS for containerised apps using an add-on - see the item above).

(It's pretty clear to me that the direction of travel for Azure Monitor is towards it becoming a fully OTLP/Prometheus/Grafana-based system, which would very much align with the current cloud-native industry standards for logging and monitoring.)

## Azure Storage

- [Entra-only identities with Azure Files (GA)](https://azure.microsoft.com/en-us/updates?id=562359) : Securely access file shares using cloud-native identities without requiring Active Directory or hybrid identity infrastructure. With Microsoft Entra ID as the authentication authority, users can access Azure Files using [Kerberos-based authentication](https://learn.microsoft.com/en-us/azure/storage/files/storage-files-identity-auth-hybrid-identities-enable?tabs=azure-portal%2Cintune#enable-cloud-only-groups-support-mandatory-for-cloud-only-identities) backed entirely by cloud identities - eliminating dependency on domain controllers and simplifying storage and identity architecture. Been a while coming, this one - it'll be useful to be able to go fully cloud-native for Azure Files access.

- [Managed Identity Support for Azure Files SMB (GA)](https://azure.microsoft.com/en-us/updates?id=562350) : [Azure Files now supports Managed Identities for SMB access](https://learn.microsoft.com/en-us/azure/storage/files/files-managed-identities?tabs=portal&pivots=windows), enabling applications and services to authenticate without storing static credentials or account keys. This feature aligns with Zero Trust principles, allowing workloads to use Entra-issued tokens for secure, short-lived access to file shares. Definite security improvement for apps using Azure Files for storage, removing the need to supply (and protect) the storage account key.

 - [Smart Tier (Azure Blob and Data Lake Storage) (GA)](https://azure.microsoft.com/en-us/updates?id=559746) : [Smart tier](https://learn.microsoft.com/en-us/azure/storage/blobs/access-tiers-smart?tabs=azure-portal) is a fully managed and automated data tiering solution, avoiding manual tier placement for object storage standard online tiers. Smart tier automatically moves your data between hot, cool, and cold access tiers based on usage patterns, optimizing your costs for these access tiers automatically. Note that smart tiering requires a GPv2 storage account and zone-redundant storage - so if the region you're in doesn't support availability zones, it can't be used. Generally available in nearly all zonal public regions, and in preview in Azure Government and China.

## Compute

- [Azure Dl/D/E v7 Virtual Machines (GA)](https://azure.microsoft.com/en-us/updates?id=560734) : Powered by the latest Intel Xeon 6 (Granite Rapids) processors, these general‑purpose and memory‑optimized VMs deliver up to 20% better general compute performance compared to previous generation Intel‑based v6 VMs, alongside major improvements in scale, networking, and storage. Dl/D/E v7 VMs are ideal for web and application servers, containerized workloads, databases, analytics, and in‑memory workloads such as SAP and Redis. ('GA' is for me slightly misleading here, as the only region these VMs are currently available in is Central US. More regions are coming soon.)

## Virtual Network Manager

- [Azure Virtual Network Manager rule impact analyzer (GA)](https://azure.microsoft.com/en-gb/updates?id=562010) : Similar to the Network Watcher update, but part of VNM for security admin rules. [Simulate the impact of your security admin rules](https://learn.microsoft.com/en-us/azure/virtual-network-manager/how-to-simulate-security-admin-rules) on your virtual networks before deploying your rules. This feature is available in the Azure portal and is powered by Azure Network Watcher traffic analytics and virtual network flow logs, providing data-driven insights into how security admin rule deployments could affect your existing virtual network traffic.

## Virtual Networks

- [Azure Virtual Network updates – default limits increased for NSGs and route tables (GA)](https://azure.microsoft.com/en-us/updates?id=562695) : The new defaults are now 2,000 security rules per NSG, 6,000 addresses or ports per NSG rule, 1,000 routes per route table, and 600 route tables per subscription. Given the ever-increasing size and complexity of Azure Virtual Network infrastructures, and the number of rules and routes needed in a complex secure setup, this update is likely to be welcome.

- [Network Watcher rule impact analyser (GA)](https://azure.microsoft.com/en-gb/updates?id=562690) : [Assess the potential impact](https://learn.microsoft.com/en-gb/azure/network-watcher/traffic-analytics-rule-impact-analyzer) of your network security group (NSG) or security admin rule changes on live network traffic before applying them. This feature is accessible through the Azure portal and leverages Azure Network Watcher traffic analytics and virtual network flow logs to deliver data-driven visibility into how NSG or network manager rule updates could influence your current network behavior. 

