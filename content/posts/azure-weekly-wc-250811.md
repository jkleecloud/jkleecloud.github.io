+++
title = 'Azure Snippets w/c 11/08/2025'
date = 2025-08-13T08:00:16+01:00
draft = true
categories = ['Azure Weekly 2025']
tags = ['DB for PostgreSQL', 'Redis', 'IaC', 'NSG', 'Application Gateway', 'Azure Backup', 'Virtual Network Manager', 'Compute', 'FinOps', 'Azure Storage']
+++

Summary of Azure snippets for the week commencing 11th August 2025, grouped by Azure service. Lots of AKS announcements this time, but one or two other service updates as well (including one that I've personally been waiting a while for!).

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [Application Gateway](#application-gateway)
- [Azure Backup](#azure-backup)
- [Azure Cache for Redis](#azure-cache-for-redis)
- [Azure DB for PostgreSQL](#azure-db-for-postgresql)
- [Azure Kubernetes Service](#azure-kubernetes-service)
- [Infrastructure as Code](#infrastructure-as-code)
- [Network Security Groups](#network-security-groups)
- [Virtual Network Manager](#virtual-network-manager)

## Application Gateway

- [Private Application Gateway on Application Gateway v2 (GA)](https://azure.microsoft.com/en-us/updates?id=500225) : I've been waiting for this feature to go GA for more than 2 years now! Finally, private deployments for the v2 Application Gateway are available. These permit: private IP only frontend configuration (no Public IP address is required for management); enhanced control over Network Security Groups (the GatewayManager inbound rules are no longer needed and you can define a 'Deny All' outbound rule to drop other traffic); and enhanced UDR support (forced tunnelling to a network appliance using the '0.0.0.0/0' rule is now supported).

## Azure Kubernetes Services


