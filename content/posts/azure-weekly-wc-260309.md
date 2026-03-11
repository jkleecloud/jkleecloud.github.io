+++
title = 'Azure Snippets w/c 09/03/2026'
date = 2026-03-11T21:00:16Z
draft = false
categories = ['Azure Weekly 2026']
tags = ['DB for PostgreSQL', 'Azure Firewall', 'AKS', 'Governance']
+++

Summary of Azure snippets for the week commencing 9th March 2026, grouped by Azure service. Seems to be a slow period for Azure updates at the moment, but I've gathered a few useful-looking items for this week.

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [Azure DB for PostgreSQL](#azure-db-for-postgresql)
- [Azure Firewall](#azure-firewall)
- [Azure Kubernetes Services](#azure-kubernetes-services)
- [Governance](#governance)

## Azure DB for PostgreSQL

- [Azure Database for PostgreSQL dashboards with Grafana (GA)](https://azure.microsoft.com/en-us/updates?id=558321) :  Azure Database for PostgreSQL users can now access [prebuilt Grafana dashboards](https://techcommunity.microsoft.com/blog/adforpostgresql/dashboards-with-grafana---now-in-azure-portal-for-postgresql/4497607) directly within the Azure portal - with no additional cost or configuration required. 

## Azure Firewall

- [Draft & Deploy on Azure Firewall (GA)](https://azure.microsoft.com/en-us/updates?id=558072) : The new [Draft & Deploy](https://learn.microsoft.com/en-us/azure/firewall/draft-deploy?tabs=portal) feature for Azure Firewall Policy introduces a streamlined, two-phase approach to managing firewall policies, significantly reducing deployment time and disruption. Traditionally, any policy update would trigger a full deployment of both the policy and the attached firewall, taking 2–4 minutes per change. With Draft & Deploy, users can collaboratively make multiple changes in a draft version cloned from the current policy without affecting the live environment. Once finalized, all changes can be deployed at once, replacing the existing policy. 

## Azure Kubernetes Services

- [Roll back node pool versions (Public Preview)](https://learn.microsoft.com/en-gb/azure/aks/roll-back-node-pool-version) : The node pool version rollback feature in Azure Kubernetes Service (AKS) enables you to recover from unexpected behaviors after Kubernetes upgrades. Until recently, 'undoing' a Kubernetes version upgrade in AKS wasn’t a first-class operation. You’d be looking at manual workarounds or blue-green setups to recover.

## Governance

- [Azure SRE Agent (GA)](https://azure.microsoft.com/en-us/updates?id=558321) : First announced [last year](https://jkleecloud.github.io/posts/azure-weekly-wc-250526/#governance), the [Azure SRE agent](https://techcommunity.microsoft.com/blog/appsonazureblog/announcing-general-availability-for-the-azure-sre-agent/4500682) is now generally available. This AI-powered operations agent helps teams improve uptime, reduce incident impact, and cut operational toil by accelerating diagnosis and automating response workflows.



