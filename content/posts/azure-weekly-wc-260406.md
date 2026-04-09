+++
title = 'Azure Snippets w/c 06/04/2026'
date = 2026-04-09T08:00:16+01:00
draft = false
categories = ['Azure Weekly 2026']
tags = ['AKS', 'Azure SQL', 'Azure Storage', 'Compute', 'Sustainability']
+++

Summary of Azure snippets for the week commencing 6th April 2026, grouped by Azure service.

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [Azure Kubernetes Services](#azure-kubernetes-services)
- [Azure SQL](#azure-sql)
- [Azure Storage](#azure-storage)
- [Compute](#compute)
- [Sustainability](#sustainability)

## Azure Kubernetes Services

- [Pod CIDR expansion in AKS (GA)](https://azure.microsoft.com/en-us/updates?id=557907) : When clusters exhaust available pod IP addresses, teams have historically been forced to rebuild environments to restore capacity, creating operational disruption. [Pod CIDR expansion](https://learn.microsoft.com/en-us/azure/aks/azure-cni-overlay-pod-expand) allows overlay‑based (e.g. CNI Overlay) AKS clusters to increase their pod IP range in place without cluster recreation. Very useful for large clusters, and can be used in conjunction with a move from e.g. kubenet to CNI Overlay networking.

- [Blue-green agent pool upgrade (Public Preview)](https://azure.microsoft.com/en-us/updates?id=557862) : In‑place node pool upgrades can introduce risk by applying changes to directly running environments. [Blue‑green agent pool upgrades](https://learn.microsoft.com/en-us/azure/aks/blue-green-node-pool-upgrade) create a parallel node pool with the new configuration, allowing validation before workloads are shifted and providing a clear rollback path. This reduces upgrade risk and supports more controlled cluster lifecycle management. Another new feature improving the experience and resilience for upgrading node pools, following last month's [node pool version rollback](https://jkleecloud.github.io/posts/azure-weekly-wc-260309/#azure-kubernetes-services) preview release.

- [Microsoft Azure Kubernetes Application Network (Public Preview)](https://azure.microsoft.com/en-us/updates?id=557922) : [Azure Kubernetes Application Network](https://learn.microsoft.com/en-us/azure/application-network/overview) introduces application‑layer abstractions for Kubernetes traffic, including mutual TLS for pod‑to‑pod communication, application‑aware authorization policies, and detailed traffic telemetry across ingress and in‑cluster communication, with built‑in multi‑region connectivity configured in a single step. This enables teams to apply identity‑aware security and gain deeper traffic insight without deploying or operating a full service mesh, reducing operational overhead while improving consistency and auditability. Based on Istio's [ambient mode](https://istio.io/latest/docs/ambient/overview/), which implements mesh functionality without requiring a sidecar running a proxy in every application pod. Currently supports [very limited regions](https://learn.microsoft.com/en-us/azure/application-network/overview#limitations) (none in the UK) and doesn't support private clusters.

- [Application routing with meshless Istio (Public Preview)](https://azure.microsoft.com/en-us/updates?id=557927) : Following the [deprecation of ingress‑nginx](https://www.kubernetes.dev/blog/2025/11/12/ingress-nginx-retirement/), Kubernetes operators need a supported, standards‑aligned migration path for ingress without the complexity of a full service mesh. Application Routing with Meshless Istio enables adoption of the Kubernetes Gateway API for ingress management while avoiding sidecar‑based architectures, and Microsoft is extending support for existing ingress‑nginx‑based Application Routing while contributing to the open‑source ingress2gateway project.

- [Container network logs (GA)](https://azure.microsoft.com/en-gb/updates?id=557892) : [Container network logs](https://learn.microsoft.com/en-us/azure/aks/container-network-observability-logs) in Azure Kubernetes Service (AKS), now generally available, provide context‑rich visibility into network flows by capturing detailed per‑flow metadata such as IPs, ports, namespaces, pod and service names, flow direction, and policy verdicts across L3/L4 and supported Layer 7 protocols including HTTP, gRPC, and Kafka. This capability supports both stored logs for continuous, filter-based collection and on-demand logs for targeted snapshots. Part of AKS Advanced Container Networking Services.

- [Container network metrics filtering (GA)](https://azure.microsoft.com/en-gb/updates?id=557902) : [Container network metrics filtering](https://learn.microsoft.com/en-us/azure/aks/container-network-observability-metrics?tabs=Cilium#container-network-metrics-filtering-preview) in Advanced Container Networking Services (ACNS) allows operators to control which container‑level network metrics are collected using Kubernetes custom resources, with filters applied dynamically. This helps teams reduce monitoring noise, manage data volumes, and keep dashboards focused on actionable signals.

- [AI Agent for container networking troubleshooting (Public Preview)](https://azure.microsoft.com/en-us/updates?id=557887) : Troubleshooting Kubernetes networking issues is often slowed by logs and metrics scattered across multiple tools, forcing engineers to manually correlate signals during incidents. The container networking agent provides a lightweight, web‑based interface that translates natural‑language problem descriptions into read‑only diagnostics using live cluster telemetry and orchestrates safe diagnostic workflows. By consolidating networking insights and summarizing findings with structured remediation guidance, the agent reduces investigation time and improves troubleshooting consistency without making configuration changes. Another feature of Advanced Container Networking Services, though the ACNS docs don't seem to have quite caught up with it yet!

## Azure SQL

- [SQL MCP Server (Public Preview)](https://azure.microsoft.com/en-us/updates?id=558150) : [SQL MCP Server](https://learn.microsoft.com/en-us/sql/mcp/) is a feature rich component of
Data API Builder (DAB) that gives you a simple, predictable, secure way to bring AI agents into your data workflows without compromising the database or relying on natural language. SQL MCP Server runs locally, on premises, or in any cloud as a containerized service.

- [GitHub Copilot in SQL Server Management Studio 22 (GA)](https://azure.microsoft.com/en-us/updates?id=558134) : With [GitHub Copilot in SSMS](https://learn.microsoft.com/en-us/ssms/github-copilot/overview), you can use natural language to develop, explain, fix, and optimize T‑SQL, troubleshoot queries, and better understand your databases without leaving your workflow. GitHub Copilot includes intelligent code completions in the query editor, helping you write T-SQL faster and with greater confidence. In addition, you can use database instructions to explain business rules and conventions that Copilot should follow, helping it to provide more precise, relevant assistance. By using the same GitHub Copilot subscription already available in Visual Studio and Visual Studio Code, you get a consistent AI experience across your daily tools — now extended to SQL databases.

## Azure Storage

- [User delegation SAS for Azure Tables, Azure Files, and Azure Queues (GA)](https://azure.microsoft.com/en-us/updates?id=559535) : Following [February's preview release](https://jkleecloud.github.io/posts/azure-weekly-wc-260202/#azure-storage), user delegation SAS for Azure Tables, Azure Files, and Azure Queues is now generally available. User delegation SAS allows users to [create a more secure SAS token](https://learn.microsoft.com/en-us/rest/api/storageservices/create-user-delegation-sas) than account or service SAS by tying the SAS token to the delegator. This extension of UDK SAS will allow users to set SAS tokens at the table, table entity, queue, queue entity, file container, and individual file level.

## Compute

- Multiple compute series retirements on 31 May 2027 - [NP](https://azure.microsoft.com/en-us/updates?id=548497), [HBv2](https://azure.microsoft.com/en-us/updates?id=548525) and [HC-series](https://azure.microsoft.com/en-us/updates?id=548543) (RET) : These are GPU and HPC VMs, now superseded by newer SKUs.

## Sustainability

- [Emissions Impact Dashboard for Azure (RET)](https://azure.microsoft.com/en-us/updates?id=558278) : Effective March 31, 2027, the Emissions Impact Dashboard for Azure hosted by Power BI will be retired. After this date, the dashboard will no longer be accessible and technical support will be discontinued. Customers can explore [Azure Carbon Optimizer](https://learn.microsoft.com/en-us/azure/carbon-optimization/) in advance of the retirement date as an alternative solution. Get your dashboard data exported if you need it for historical reporting!