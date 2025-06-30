+++
title = 'Azure Snippets w/c 30/06/2025'
date = 2025-06-30T08:00:16+01:00
draft = false
categories = ['Azure Weekly 2025']
tags = ['Azure Advisor', 'Azure Firewall', 'Compute', 'Copilot', 'FinOps', 'Virtual Network Manager']
+++

Summary of Azure snippets for the week commencing 30th June 2025, grouped by Azure service. After the huge flurry of announcements around Build, things have been a bit quieter on the Azure front, so a short and sweet post this time!

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [Azure Advisor](#azure-advisor)
- [Azure Firewall](#azure-firewall)
- [Compute](#compute)
- [Copilot](#copilot)
- [FinOps](#finops)
- [Virtual Network Manager](#virtual-network-manager)

## Azure Advisor

- [Azure Advisor VM Right-Sizing Update – Expanded SKU support and series coverage (GA)](https://azure.microsoft.com/en-gb/updates?id=493047) : Azure Advisor has improved its VM right-sizing recommendations by extending coverage for newer VM series. This broader SKU coverage across the D, E, and F VM families enables a more comprehensive evaluation of CPU performance, providing your teams with recommendations to optimize workloads efficiently.

## Azure Firewall

- [Draft & Deploy for Policy (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=496523) : With [Draft & Deploy](https://learn.microsoft.com/en-us/azure/firewall/draft-deploy?tabs=portal), users can collaboratively make multiple changes to an Azure Firewall Policy in a draft version cloned from the current policy without affecting the live environment. Once finalized, all changes can be deployed at once, replacing the existing policy. Minimises the number of redeployments needed to update a policy, each of which could trigger an update of the whole firewall.

## Compute

- [Azure FXv2-series Virtual Machines (GA)](https://azure.microsoft.com/en-gb/updates?id=492651) : [Latest offering](https://techcommunity.microsoft.com/blog/azurecompute/announcing-the-general-availability-of-azure-fxv2-series-virtual-machines/4414399?previewMessage=true) in the [compute-optimised VM families](https://learn.microsoft.com/en-us/azure/virtual-machines/sizes/compute-optimized/fxmsv2-series?tabs=sizebasic), offering a high CPU-to-memory ratio. Targeted at compute-intensive workloads such as databases and data analytics.

## Copilot

- [Azure WAF integration in Microsoft Security Copilot (GA)](https://azure.microsoft.com/en-gb/updates?id=496536) : This integration supports both Azure Front Door WAF and Azure Application Gateway WAF. By [integrating Azure WAF with Security Copilot](https://learn.microsoft.com/en-gb/azure/web-application-firewall/waf-copilot), organizations can streamline security operations, and accelerate investigations, helping security teams stay ahead of increasingly sophisticated threats. Key features in GA include: SQL Injection (SQLi) Attack Analysis; Cross-Site Scripting (XSS) Attack Analysis; Top Offending IP Analysis; Top Azure WAF Rules Analysis.

## FinOps

- [Cost Management support for FOCUS 1.2 (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=496981) : Microsoft Cost Management now supports exporting cost and usage data in the [FinOps Open Cost and Usage Specification (FOCUS)](https://focus.finops.org/focus-specification/) 1.2 schema. This update introduces key enhancements that help FinOps teams streamline reporting, unify billing data across clouds, and enable consistent multi-currency financial analysis.

## Virtual Network Manager

- [Azure Virtual Network Manager IP address management (GA)](https://azure.microsoft.com/en-gb/updates?id=484347) : In complex network environments, managing IP addresses effectively is essential. This feature [centralises IP planning and allocation](https://learn.microsoft.com/en-us/azure/virtual-network-manager/concept-ip-address-management), allowing users to automatically assign non-overlapping addresses, reserve IPs for specific needs, and prevent conflicts between Azure, on-premises, and multi-cloud address spaces. It also provides clear insights into IP usage and allocation across your network resources - which can be very difficult to obtain in a large Azure environment, particularly if subnets are being deployed and managed by other Azure services. GA in UK South, in preview in UK West.