+++
title = 'Azure Snippets w/c 06/10/2025'
date = 2025-10-08T08:00:16+01:00
draft = true
categories = ['Azure Weekly 2025']
tags = ['DB for PostgreSQL', 'Redis', 'IaC', 'NSG', 'Application Gateway', 'Azure Backup', 'Virtual Network Manager', 'Compute', 'FinOps', 'Azure Storage']
+++

Summary of Azure snippets for the week commencing 6th October 2025, grouped by Azure service.

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

- [Backend TLS validation controls (GA)](https://azure.microsoft.com/en-us/updates?id=503393) : Application Gateway now supports the following configurable options, giving customers greater flexibility in managing [backend TLS behaviour](https://learn.microsoft.com/en-us/azure/application-gateway/configuration-http-settings?tabs=backendhttpsettings#backend-https-validation-settings) across diverse environments: Enable or disable Certificate chain and expiry verification; Enable or disable SNI verification. With these new settings, customers can customize TLS validations to align with their infrastructure needs.

- [Dedicated connections to backends (GA)](https://azure.microsoft.com/en-us/updates?id=503398) : By default, Application Gateway reuses the idle backend connections to optimize the resource usage of TCP connections helping both the gateway and the backend servers. With the [dedicated connection setting](https://learn.microsoft.com/en-us/azure/application-gateway/configuration-http-settings?tabs=backendhttpsettings#dedicated-backend-connection), each incoming client connection is mapped to a distinct backend connection, ensuring one-to-one communication between the frontend and the backend. 

## Redis

- [Azure Cache for Redis SKUs retiring (RET)](https://techcommunity.microsoft.com/blog/azure-managed-redis/azure-cache-for-redis-retirement-what-to-know-and-how-to-prepare/4458721) : With [Azure Managed Redis having gone GA](https://azure.microsoft.com/en-gb/updates?id=467264) in May 2025, Microsoft is [retiring Cache for Redis](https://learn.microsoft.com/en-gb/azure/azure-cache-for-redis/cache-whats-new#october-2025). Basic, Standard and Premium will be retired in September 2028, Enterprise and Enterprise Flash in March 2027; with new instance creation blocked from 1 April 2026. Check out the [retirement FAQ](https://learn.microsoft.com/en-gb/azure/azure-cache-for-redis/retirement-faq) and start [planning for migration](https://learn.microsoft.com/en-gb/azure/redis/migrate/migrate-overview) to Managed Redis.
 