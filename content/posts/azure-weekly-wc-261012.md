+++
title = 'Azure Snippets w/c 12/10/2025'
date = 2026-10-13T08:00:16+01:00
draft = true
categories = ['Azure Weekly 2026']
tags = ['DB for PostgreSQL', 'Redis', 'IaC', 'NSG', 'Application Gateway', 'Azure Backup', 'Virtual Network Manager', 'Compute', 'FinOps', 'Azure Storage']
+++

Summary of Azure snippets for the week commencing 12th October 2026, grouped by Azure service.

(Any editorial blurb goes here :-)

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [Application Gateway](#application-gateway)
- [Azure Backup](#azure-backup)
- [Azure Cache for Redis](#azure-cache-for-redis)
- [Azure DB for PostgreSQL](#azure-db-for-postgresql)
- [Azure Kubernetes Services](#azure-kubernetes-services)
- [Infrastructure as Code](#infrastructure-as-code)
- [Network Security Groups](#network-security-groups)
- [Virtual Network Manager](#virtual-network-manager)

## Compute

- [Dv3, Dsv3, Ev3, and Esv3 Azure VMs retiring (RET)](https://azure.microsoft.com/en-us/updates?id=572346) : Microsoft is announcing the retirement of the Dv3, Dsv3, Ev3, and Esv3 Azure VM series in public cloud Azure regions. These VMs will enter the [End-of-Life lifecycle stage](https://learn.microsoft.com/en-us/azure/virtual-machines/sizes/lifecycle/lifecycle-overview) and retire on November 15, 2029. [Migration to the equivalent v5 series](https://learn.microsoft.com/en-us/azure/virtual-machines/sizes/lifecycle/sizes-v5-modernization-overview) is the simplest path forward; [migrating to v6 or v7](https://learn.microsoft.com/en-us/azure/virtual-machines/sizes/lifecycle/sizes-v6-v7-modernization-overview) requires upgrading the VM generation to Gen 2 and enabling Trusted Launch, which is more involved.

- [Microsoft Dev Box will be retired on September 18, 2028 (RET)](https://azure.microsoft.com/en-us/updates?id=567933) : RIP Dev Box - close-down began on 14th September 2026, it's no longer being developed as a service, and will be retiring in September 2028. Windows 365 is the way forward for virtualised Dev environments.

- [Azure Deployment Environments will be retired on February 22, 2027 (RET)](https://azure.microsoft.com/en-us/updates?id=567934) : Probably connected to the retirement of Dev Box, Azure Deployment Environments began closing down on 14th September 2026 and will be retired on 22nd Feb 2027. Not so clear what the recommended migration path is - a service or services will be needed to cover environment provisioning and developer self-service.

## Microsoft Foundry / AI

- 

