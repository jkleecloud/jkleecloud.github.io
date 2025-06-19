+++
title = 'Azure Snippets w/c 16/06/2025'
date = 2025-06-20T08:00:16+01:00
categories = ['Azure Weekly 2025']
tags = ['APIM', 'Azure Backup', 'Azure Command Launcher', 'Azure DB for PostgreSQL', 'Azure Functions', 'Azure SQL', 'Azure SQL Managed Instance']
+++

Summary of Azure snippets for the week commencing 16th June 2025, grouped by Azure service. After the flurry of announcements from and around Build, it's a little quieter this week :-)

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [API Management](#api-management)
- [Azure Backup](#azure-backup)
- [Azure Command Launcher](#azure-command-launcher)
- [Azure DB for PostgreSQL](#azure-db-for-postgresql)
- [Azure Functions](#azure-functions)
- [Azure SQL](#azure-sql)

## API Management

- [Import from Azure AI Foundry to Azure API Management’s AI Gateway (GA)](https://azure.microsoft.com/en-gb/updates?id=491980) : This capability simplifies [onboarding of large language model (LLM) APIs](https://learn.microsoft.com/en-us/azure/api-management/azure-openai-api-from-specification) by enabling seamless integration through the Azure portal.

## Azure Backup

- [Increased Disk Capacity for Azure VM Backup (GA)](https://azure.microsoft.com/en-gb/updates?id=496651) : VMs can now be protected with [individual disks up to 64 TB and a total of 512 TB per VM](https://learn.microsoft.com/en-us/azure/backup/backup-support-matrix#azure-vm-backup-support). This enables large disk support for business continuity and recovery from disasters or ransomware attacks. Reduces the need to exclude disks from a backup set to get a VM backup if you're still running VMs with lots of disks.

## Azure Command Launcher

- [Azure Command Launcher for Java (Private Preview)](https://azure.microsoft.com/en-gb/updates?id=496173) : Announcing the private preview of [jaz, a new JVM launcher optimized specifically for Azure](https://techcommunity.microsoft.com/blog/appsonazureblog/announcing-azure-command-launcher-for-java/4420278). By setting JVM parameters tailored for cloud deployments, jaz reduces wasted memory and CPU cycles, improves first-deploy performance, and enhances cost efficiency. This is ideal for developers who want better JVM defaults without diving deep into JVM tuning guides, and  develop and deploy cloud-native microservices. Works with cloud-native and container workloads.

## Azure DB for PostgreSQL

- [In-place major version upgrade to PostgreSQL 17 on Azure Database for PostgreSQL flexible server (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=495135) : You can now [upgrade your Azure Database for PostgreSQL flexible server instance to PostgreSQL 17](https://techcommunity.microsoft.com/blog/adforpostgresql/postgresql-17-in-place-upgrade-%E2%80%93-now-in-public-preview/4413946) using a simple, in-place upgrade — now available in public preview. This release allows you to move from previous PostgreSQL versions (14, 15, or 16) to PostgreSQL 17 without changing your server endpoint, reconfiguring your application, or performing manual data migration.

## Azure Functions

- [OpenTelemetry support (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=496415) : Expanding on the limited preview announced last year, these enhancements deliver [better observability](https://learn.microsoft.com/en-us/azure/azure-functions/opentelemetry-howto?tabs=app-insights&pivots=programming-language-csharp), improved performance, and more detailed insights into your function executions, helping you diagnose issues faster and optimize your applications more effectively. For those already using OTEL with tools like Prometheus and Grafana, this makes it easier to integrate Azure Functions into your monitoring.

## Azure SQL

- [Azure SQL Managed Instance faster management operations (GA)](https://azure.microsoft.com/en-gb/updates?id=496292) : You can now create and update your Azure SQL Managed Instance with improved speed and precision. The new faster [management operations experience](https://learn.microsoft.com/en-us/azure/azure-sql/managed-instance/management-operations-overview?view=azuresql) enhances elasticity by enabling you to provision any configuration of your instance in under 30 minutes — whether it uses default or custom settings. Update and scaling operations are similarly accelerated, completing in less than 60 minutes compared to the previous four-hour process. Applies to all service tiers, but not to zone-redundant instances.

- [Flexible memory in Azure SQL Managed Instances (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=491047) : A new [customizable memory option](https://techcommunity.microsoft.com/blog/azuresqlblog/unlocking-more-power-with-flexible-memory-in-azure-sql-managed-instance/4425054) helps you optimize costs in Azure SQL Managed Instance. Now you can independently configure RAM from the vCores, helping you to save on compute and licensing costs. This feature is available exclusively in the Next-gen General Purpose tier for Premium-series hardware.
