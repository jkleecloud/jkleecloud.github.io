+++
title = 'Azure Snippets w/c 02/12/2024'
date = 2024-12-05T10:50:44Z
draft = true
categories = ['Azure Weekly 2024']
tags = ['API Center', 'Azure Bastion', 'Chaos Studio', 'DB for PostgreSQL', 'AKS', 'Azure Local', 'Dev Box', 'Network Security Perimeter', 'Azure SQL', 'APIM', 'Extended Zones', 'Redis']
+++

Summary of Azure snippets for the week commencing 2nd December 2024, grouped by Azure service.

It's been a little while since I posted, and this one is a bit of a bumper one with MS Ignite having finished recently - a lot of Azure updates have dropped, along with other products. AI is unsurprisingly a big theme once again :-) Check out the [Ignite 2024 Book of News](https://news.microsoft.com/ignite-2024-book-of-news/) for all the details.

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/en-gb/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [API Center](#api-center)
- [API Management](#api-management)
- [Azure Bastion](#azure-bastion)
- [Azure Chaos Studio](#azure-chaos-studio)
- [Azure DB for PostgreSQL](#azure-db-for-postgresql)
- [Azure Extended Zones](#azure-extended-zones)
- [Azure Kubernetes Service](#azure-kubernetes-service)
- [Azure Local](#azure-local)
- [Azure SQL](#azure-sql)
- [Dev Box](#dev-box)
- [Network Security Perimeter](#network-security-perimeter)
- [Redis](#redis)

## API Center

- [API Center Plugin for GitHub Copilot for Azure (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=469053) : With the public preview of the API Center plugin, you can now leverage GitHub Copilot for Azure for a variety of API-related tasks, including designing and generating API specs. Seems to be part of the [API Center VS Code extension](https://marketplace.visualstudio.com/items?itemName=apidev.azure-api-center).
 - [API Management & API Center Synchronization (GA)](https://azure.microsoft.com/en-us/updates?id=468067) : A fast turnaround for this one - it only [went into preview in October](../azure-weekly-wc-241028)! You can now easily select an API Management instance to sync directly to API Center. This synchronization enables streamlined API discovery, centralized tracking, and enhanced governance across your organization’s APIs.

## API Management

- [Shared workspace gateways (GA)](https://azure.microsoft.com/en-us/updates?id=467802) : This new feature introduces the ability to associate [multiple workspaces with a single workspace gateway](https://techcommunity.microsoft.com/blog/integrationsonazureblog/announcing-general-availability-of-shared-workspace-gateways-in-azure-api-manage/4292221), offering a cost-effective way to federate API management. With [workspaces](https://techcommunity.microsoft.com/blog/integrationsonazureblog/announcing-general-availability-of-workspaces-in-azure-api-management/4210796) (which went GA in August), organisations can empower API teams to independently manage their APIs, while centralising oversight and unifying API discovery through the developer portal. By connecting up to thirty workspaces to one gateway, you can now achieve these benefits at a significantly lower cost.
- [Premium v2 Tier (Public Preview)](https://azure.microsoft.com/en-us/updates?id=467808) : [This Premium tier](https://techcommunity.microsoft.com/blog/integrationsonazureblog/announcing-the-public-preview-of-the-premium-v2-tier-of-azure-api-management/4305897) is designed for organisations requiring enhanced performance, greater entity limits, unlimited API requests, and flexible networking options to meet the demands of modern, large-scale API environments. The [Premium v2 tier](https://learn.microsoft.com/en-gb/azure/api-management/v2-service-tiers-overview) builds on the strengths of the classic Premium offering, bringing advanced capabilities and increased flexibility for organisations operating robust API programs. Note that the public preview is limited-access currently and requires signup.

## Azure Backup

- [Secure by default with vault soft delete (Public Preview)](https://azure.microsoft.com/en-us/updates?id=469143) : Secure by default with soft delete for Azure Backup enables you to recover your backup data even after it's deleted. By enabling soft delete at vault level, we are now providing a 'secure by default' promise for all customers where all backup data will be recoverable by default for 14 days.
- [Vaulted Backup support in Azure Backup for AKS (GA)](https://azure.microsoft.com/en-us/updates?id=469695) : Now you can store backups of AKS clusters (backup data, not just metadata) [in the Backup Vault](https://learn.microsoft.com/en-us/azure/backup/azure-kubernetes-service-backup-overview#which-backup-storage-tier-does-aks-backup-support). This enables scenarios such as cross-region DR and long-term backup retention. Great to have this available alongside the Operational tier backups (stored locally).

## Azure Bastion

- [Azure Bastion Premium SKU (GA)](https://azure.microsoft.com/en-gb/updates?id=469288) : [Azure Bastion Premium](https://learn.microsoft.com/en-us/azure/bastion/bastion-overview#sku) is a new SKU to target customers handling highly sensitive virtual machine workloads. Its mission is to offer enhanced security features that ensure customer virtual machines are connected securely and to monitor VMs for any anomalies that may arise. Looks like this is 'v1' and more Premium features will come later.

## Azure Chaos Studio

- [Support for faults for AKS clusters using managed identity authentication (GA)](https://azure.microsoft.com/en-gb/updates?id=467714) : [Azure Chaos Studio](https://learn.microsoft.com/en-us/azure/chaos-studio/)’s faults for Azure Kubernetes Service clusters [now work with managed identity authentication](https://learn.microsoft.com/en-us/azure/chaos-studio/chaos-studio-aks-authentication?tabs=azure-portal). Previously, local authentication through the Kubernetes API server was the only supported authentication method.

## Azure DB for PostgreSQL

- [On-demand backups for Azure Database for PostgreSQL - Flexible Server (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=467509) : Now you can create physical snapshots of Azure Database for PostgreSQL - Flexible Server based on your business needs. This feature complements the scheduled automated backups offered by the service, while adding the flexibility to delete the on-demand backups to help you manage costs effectively. Useful for testing, upgrades etc. when you want a very recent backup available. [Documentation](https://learn.microsoft.com/en-us/azure/postgresql/flexible-server/concepts-backup-restore#on-demand-backups-preview).
- [Performance management server parameters now modifiable in Azure Database for PostgreSQL (GA)](https://azure.microsoft.com/en-us/updates?id=470452) : You can now modify multiple performance management [server parameters](https://learn.microsoft.com/en-us/azure/postgresql/flexible-server/concepts-server-parameters) in Azure Database for PostgreSQL – Flexible Server.
- [Azure Database for PostgreSQL – Flexible Server network monitoring metrics (Public Preview)](https://azure.microsoft.com/en-us/updates?id=470447) : With these enhancements, you can now gain deeper insights into network activities at the virtual machine level, helping you effectively identify and address network-related issues more quickly. [These new metrics](https://learn.microsoft.com/en-gb/azure/postgresql/flexible-server/concepts-monitoring#traffic) — including TCP Connection Backlog and Postmaster Process CPU Usage — provide actionable data that enhances the stability and reliability of your services.

## Azure Extended Zones

- [Los Angeles Extended Zone (GA) ](https://azure.microsoft.com/en-us/updates/?id=467733): Azure Extended Zones are small-footprint extensions of Azure placed in metros, industry centers, or a specific jurisdiction to serve low latency and data residency workloads. They support virtual machines (VMs), containers, storage, and a selected set of Azure services and can run latency-sensitive and throughput-intensive applications close to end users and within approved data residency boundaries. LA zone was announced [in preview in August](../azure-weekly-wc-240805/).

## Azure Kubernetes Service

- [Network isolated cluster in AKS (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=466980) : AKS now provides the option to use network isolated clusters to simplify the process of restricting network access and reduce the risk of unintentional exposure of the cluster's public endpoints to prevent security breaches. Outbound network traffic control for AKS without having to use Azure Firewall - see [the docs](https://learn.microsoft.com/en-gb/azure/aks/concepts-network-isolated) for more details.
- [Web Application Firewall (WAF) running on Application Gateway for Containers (Private Preview)](https://azure.microsoft.com/en-gb/updates?id=468587) : Application Gateway for Containers now supports Web Application Firewall (WAF) in private preview. You need to sign up for this one.
- [Upgrade algorithm improvements in AKS (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=467872) : AKS upgrades currently fail when encountering a Pod drain failure. To improve upgrade efficiency, a new algorithm is being introduced. It allows you to [configure upgrades](https://learn.microsoft.com/en-us/azure/aks/upgrade-cluster?tabs=azure-cli#optimize-for-undrainable-node-behavior-preview) so that if a node is blocked, AKS will use any available surge capacity to continue upgrading other nodes, labeling the blocked node as 'quarantined' (cordoned).
- [Auto instrumentation for AppInsights in AKS (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=467977) : Auto-instrumentation enables Application Insights to make telemetry like metrics, requests, and dependencies available in your Application Insights resource. It provides easy access to Application performance monitoring (APM) experiences such as the application dashboard and application map. Auto-instrumentation automatically injects the Azure Monitor OpenTelemetry distro into your application pods to generate application monitoring telemetry. This preview supports NET, Java, and JavaScript (Node.js). Support for Python is coming soon.
- [AKS Security Dashboard (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=467986) : Offers full visibility over the vulnerabilities of runtime and host in your AKS cluster, by adding a Defender for Cloud blade into the AKS settings in the Azure portal. Presumably you will need to have the Defender for Containers plan enabled to make full use of this!
- [Kubernetes Metadata and Logs Filtering in Azure Monitor - Container Insights (GA)](https://azure.microsoft.com/en-us/updates?id=469519) : [Kubernetes metadata and logs filtering](https://learn.microsoft.com/en-us/azure/azure-monitor/containers/container-insights-logs-schema#kubernetes-metadata-and-logs-filtering) extends the ContainerLogsV2 schema with additional Kubernetes metadata. The logs filtering feature provides filtering capabilities for both workload and platform containers. These features give you richer context and improved visibility into your workloads.

## Azure Local

- [Azure Local (GA)](https://azure.microsoft.com/en-gb/updates?id=467372) : This is the [next evolution of Azure Stack](https://learn.microsoft.com/en-gb/azure/azure-local/rename-to-azure-local), tying on-prem infrastructure in to the Azure cloud via Azure Arc. Lots of information available in the [Azure Arc blog post](https://techcommunity.microsoft.com/blog/azurearcblog/introducing-azure-local-cloud-infrastructure-for-distributed-locations-enabled-b/4296017) and the [Ignite book of news article](https://news.microsoft.com/ignite-2024-book-of-news/#a-331-azure-expands-adaptive-cloud-introduces-azure-local-infrastructure-solution-).

## Azure SQL

- [Managed Instance mirroring to Azure Fabric (Public Preview)](https://azure.microsoft.com/en-us/updates?id=467768) : You can now use [mirroring](https://learn.microsoft.com/en-us/fabric/database/mirrored-database/azure-sql-database-tutorial) to easily replicate Azure SQL Managed Instance data to Microsoft Fabric. Mirroring replicates your data in near real-time directly into Fabric OneLake.
- [Managed Instance Pools (GA)](https://azure.microsoft.com/en-us/updates?id=467773) : [Instance pools](https://techcommunity.microsoft.com/blog/azuresqlblog/azure-sql-managed-instance-pools-general-availability/4304474) give you a [flexible way](https://learn.microsoft.com/en-us/azure/azure-sql/managed-instance/instance-pools-overview?view=azuresql) to deploy compute resources for Azure SQL Managed Instance. You can deploy cost-effective, two-vCore instances, providing an ideal platform as a service (PaaS) target for small instances when migrating SQL Server to Azure or when running your existing Azure SQL Managed Instance fleet. You can resize an instance pool or use it to contain instances of different sizes. You can also move instances in or out of pools. 2-vCore granularity at the moment, so it really is for small instances right now - be interesting to see if it develops wider.

## Dev Box

- [New features (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=468062) : New features in Dev Box that make it easier to configure task-based workstations for development teams and enhance project guardrails. Includes team customisations (Dev team leads can create project-based configurations for their entire team, with the tools, packages and settings in a single config file), imaging (team customisations can be converted to images) and Project Policy (IT Admins can set up guardrails around resources that projects can and cannot access, such as images, SKUs, and network connections). Lots of details behind these - check out the [Ignite blog post](https://devblogs.microsoft.com/develop-from-the-cloud/devboxignite2024/) for more info. (There are also [new features in Deployment Environments](https://azure.microsoft.com/en-gb/updates?id=468076), which is a [complementary service to Dev Box](https://learn.microsoft.com/en-gb/azure/deployment-environments/overview-what-is-azure-deployment-environments#components-shared-with-microsoft-dev-box), for [templated project infrastructure](https://devblogs.microsoft.com/develop-from-the-cloud/adeignite2024/).)

## Network Security Perimeter

- [Network Security Perimeter (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=469298) : Network Security Perimeter allows organisations to define a logical network isolation boundary for PaaS resources (for example, Azure Storage account and SQL Database server) that are deployed outside your organisation’s virtual networks. It restricts public network access to PaaS resources within the perimeter; exemptions can be granted by using explicit access rules for public inbound and outbound. Looks like it builds on resources like Private Link and the ideas of NSGs and resource firewalls, to allow you to create a 'secure enclave' for PaaS resources. Interestingly, it onboards PaaS resources by 'learning' access patterns. Preview is available in all public regions, but the associated Log Analytics workspace can only be in 1 of 6 US regions at present. Check out [the documentation](https://learn.microsoft.com/en-us/azure/private-link/network-security-perimeter-concepts) for more details.

## Redis

- [Azure Managed Redis (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=467264) : [Azure Managed Redis](https://learn.microsoft.com/en-us/azure/azure-cache-for-redis/managed-redis/managed-redis-overview) brings the latest Redis innovations with enhanced availability while being more cost-effective. Features 4 new tiers to match performance and memory requirements. A more 'SaaS' version of Redis than the Cache for Redis service? Interestingly, there is a [documented migration path](https://learn.microsoft.com/en-us/azure/azure-cache-for-redis/migrate/migrate-overview) to move from Cache for Redis to Managed Redis, so maybe Managed Redis is the way forward for Redis on Azure - though Cache for Redis is still getting developments such as new tiers, so I suspect they'll co-exist at least for the immediate future (or perhaps Managed Redis will take over for all the tiers below Enterprise that Cache for Redis supports, since the migration path doesn't mention the Enterprise tier?). [Managed Redis seems to support more features](https://learn.microsoft.com/en-us/azure/azure-cache-for-redis/migrate/migrate-overview#feature-comparison-between-azure-cache-for-redis-and-azure-managed-redis-preview) at a glance - including some at all tiers that you previously had to use Premium Cache for Redis to get.