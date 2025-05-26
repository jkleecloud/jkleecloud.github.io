+++
title = 'Azure Snippets w/c 19/05/2025'
date = 2025-05-26T14:00:16+01:00
draft = false
categories = ['Azure Weekly 2025']
tags = ['Azure Backup', 'Azure Bastion', 'Azure Functions', 'Azure Site Recovery', 'Azure Storage', 'Cloud Services', 'Compute', 'Copilot', 'DB for PostgreSQL', 'FinOps', 'Governance', 'IaC']
+++

Summary of Azure snippets for the week commencing 19th May 2025, grouped by Azure service.

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [Azure Backup](#azure-backup)
- [Azure Bastion](#azure-bastion)
- [Azure DB for PostgreSQL](#azure-db-for-postgresql)
- [Azure Functions](#azure-functions)
- [Azure Site Recovery](#azure-site-recovery)
- [Azure Storage](#azure-storage)
- [Cloud Services](#cloud-services)
- [Compute](#compute)
- [Copilot](#copilot)
- [FinOps](#finops)
- [Governance](#governance)
- [Infrastructure as Code](#infrastructure-as-code)


## Azure Backup

- [Vaulted backup for Azure Data Lake Storage (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=488835) : Azure Backup now supports [transferring your Azure Data Lake Storage backups to a vault](https://learn.microsoft.com/en-us/azure/backup/azure-data-lake-storage-backup-overview). In this limited public preview, you can configure vaulted backups for block blobs in a HNS-enabled standard general-purpose v2 ADLS Gen2 storage account in [specific regions](https://learn.microsoft.com/en-us/azure/backup/azure-data-lake-storage-backup-support-matrix#supported-regions) (a very limited set at present).

 - [Support in Azure Backup for AKS for Azure File Share-based Persistent Volumes (Private Preview)](https://azure.microsoft.com/en-gb/updates?id=488905) : With this new capability, customers can now enable snapshot-based backups for AKS applications using both Azure Disks and Azure file shares as persistent storage — expanding protection coverage for stateful workloads on AKS. Customers need to sign up to get onto the preview. This has been a gap in Backup for AKS for a while - nice to see it's moving towards being filled.

## Azure Bastion

- [Azure Bastion Developer now in 36 public regions (GA)](https://azure.microsoft.com/en-gb/updates?id=489004) : Previously available in 6 limited regions, [Azure Bastion Developer](https://learn.microsoft.com/en-us/azure/bastion/quickstart-developer) has now expanded to a total of 36 public regions with support for more regions coming soon. Bastion Developer provides secure-by-default RDP/SSH connectivity to VMs without the need for a public IP — all for free. Both UK regions are now supported - though VNet peering isn't (currently).

## Azure DB for PostgreSQL

- [On-Demand Backups for Azure Database for PostgreSQL – Flexible Server (GA)](https://azure.microsoft.com/en-gb/updates?id=485508) : Now you can create physical snapshots of Azure Database for PostgreSQL – Flexible Server based on your business needs. This new feature complements the scheduled automated backups offered by the service, while adding the flexibility to delete the on-demand backups. Very useful, as previously only automated backups of the server were available. [More info in the docs](https://learn.microsoft.com/en-gb/azure/postgresql/flexible-server/concepts-backup-restore#on-demand-backups), along with some limitations to be aware of.

- [Fabric Mirroring for Azure Database for PostgreSQL - Flexible Server (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=487464) : DB for PostgreSQL Flexible Servers [can now be mirrored into Fabric](https://techcommunity.microsoft.com/blog/adforpostgresql/announcing-mirroring-for-azure-database-for-postgresql-in-microsoft-fabric-for-p/4396750), alongside Azure SQL (Managed Instance coming soon) and Snowflake. Easily unify your organizational data in OneLake, enhance app integration with rich business insights by joining data across various sources, and enjoy one-click integration with Microsoft Power BI.

## Azure Functions

- [Durable Task Scheduler for Azure Functions (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=486398) : [Durable task scheduler](https://techcommunity.microsoft.com/blog/appsonazureblog/announcing-the-public-preview-launch-of-azure-functions-durable-task-scheduler/4389670) is a new storage provider for durable functions. It is designed to address the challenges and gaps identified by our customers with existing bring-your-own storage options. This is the preferred managed backend solution for customers who require high performance, enhanced monitoring of stateful orchestrations, or find managing bring-your-own storage accounts too cumbersome. Good to finally be moving towards an option beyond BYOS!

## Azure Site Recovery

- [Azure Site Recovery for Shared Disk (GA)](https://azure.microsoft.com/en-gb/updates?id=490583) : Enables you to [protect, monitor, recover, and re-protect your workloads](https://learn.microsoft.com/en-us/azure/site-recovery/tutorial-shared-disk) running on Windows Server Failover Clusters (WSFC) on Azure VMs with Shared Disks.

## Azure Storage

- [Performance Plus for Azure Disk Storage (GA)](https://azure.microsoft.com/en-gb/updates?id=488830) : Azure Disk Storage now offers [Performance Plus](https://learn.microsoft.com/en-gb/azure/virtual-machines/disks-enable-performance?tabs=azure-cli), which enhances the IOPS and throughput performance of Premium SSD, Standard SSD, and Standard HDD disks that are sized 513GB or larger. Performance Plus is offered for free and is available to use through deployments on Azure Command-Line Interface (CLI), PowerShell and the Azure Portal. You need to create a new disk to use it, so snapshots will be needed to upgrade existing disks.

- [Azure Premium SSD v2 now available in more regions (GA)](https://azure.microsoft.com/en-gb/updates?id=491675) : Multiple non-Availability Zone regions, including UK West.

## Cloud Services

- [Cloud Services (Extended Support) to Be Retired on March 31, 2027 (RET)](https://azure.microsoft.com/en-gb/updates?id=486344) : I think this is the last of the Service Manager (classic) model finally saying goodbye. Who remembers working with Web and Worker roles? Get them [migrated to Service Fabric managed clusters](https://learn.microsoft.com/en-gb/azure/service-fabric/service-fabric-cloud-services-migration-worker-role-stateless-service) if you still have any hanging round.

## Compute

- [D, Ds, Dv2, Dsv2, and Ls Series Virtual Machines to Be Retired on May 1, 2028 (RET)](https://azure.microsoft.com/en-gb/updates?id=485569) : One of the early VM SKUs finally being put out to pasture. [Migration guides are available](https://learn.microsoft.com/en-us/azure/virtual-machines/migration/sizes/d-ds-dv2-dsv2-ls-series-migration-guide) - for most customers, it should just be a matter of resizing the VM to a more recent SKU.

- [Instance Mix for Virtual Machine Scale Sets (GA)](https://azure.microsoft.com/en-gb/updates?id=486819) : Scale sets previously had to contain VMs of the same SKU. [Instance mix](https://learn.microsoft.com/en-us/azure/virtual-machine-scale-sets/instance-mix-overview) allows you to specify multiple VM sizes within a single Virtual Machine Scale Set, providing [greater flexibility and cost efficiency](https://techcommunity.microsoft.com/blog/azurecompute/general-availability-instance-mix-for-virtual-machine-scale-sets-with-flexible-o/4406386). To further optimize deployments, instance mix allows you to specify an allocation strategy to optimize for price or capacity.  

## Copilot

- [Microsoft Copilot in Azure (GA)](https://azure.microsoft.com/en-gb/updates?id=488069) : With Microsoft Copilot in Azure, you can gain new insights, discover more benefits of the cloud, and orchestrate across both cloud and edge. Copilot leverages Large Language Models (LLMs), the Azure control plane, and insights about your Azure environment to help you work more efficiently. Currently free, might be charged for later, and if you overuse it expect to be throttled :-) Also GA now - [networking capabilities for Copilot](https://azure.microsoft.com/en-gb/updates?id=487522).

## FinOps

- [Enhanced Cost Management Exports (GA)](https://azure.microsoft.com/en-gb/updates?id=491498) : Enhanced Cost Management exports are now generally available across all Azure regions and clouds, including support for the FinOps Open Cost and Usage Specification (FOCUS) format version 1.0. These updates help organizations streamline FinOps workflows, manage costs at scale, and align with enterprise security and compliance requirements.

## Governance

- [Microsoft completes landmark EU Data Boundary, offering enhanced data residency and transparency (GA)](https://blogs.microsoft.com/on-the-issues/2025/02/26/microsoft-completes-landmark-eu-data-boundary-offering-enhanced-data-residency-and-transparency/) : With the [completion of the boundary](https://www.microsoft.com/en-us/trust-center/privacy/european-data-boundary-eudb?msockid=3cf3cb184ba5674a3504de074a88665c), European commercial and public sector customers are now able to store and process their customer data and pseudonymized personal data for Microsoft core cloud services — including Microsoft 365, Dynamics 365, Power Platform, and most Azure services — within the EU and EFTA regions. In addition, Microsoft will store professional services data from technical support interactions for the core cloud services within the EU and EFTA regions. For those who use Azure in EU countries and have strict data residency requirements, this is pretty significant, as essentially all data interactions end-to-end will now be kept within the boundaries of the EU.

- [Metrics Usage Insights (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=490727) : [Metrics usage insights](https://learn.microsoft.com/en-us/azure/azure-monitor/metrics/metrics-usage-insights?tabs=portal) gives you actionable insights into metrics usage and cost optimization opportunities for your Azure monitor workspace. By providing information on time series and event usage, throttling limits, metrics usage trends, and unused metrics, you can take such actions as removing unused metrics and right-sizing resources. Currently designed for Azure Managed Prometheus users.

## Infrastructure as Code

- [Support for Desired State Configuration Extension for Azure Virtual Machines to Be Retired on March 31, 2028 (RET)](https://azure.microsoft.com/en-gb/updates?id=485828) : The [PowerShell DSC extension is being replaced](https://learn.microsoft.com/en-us/azure/governance/machine-configuration/whats-new/migrating-from-dsc-extension) by Azure Machine Configuration. [Machine Configuration](https://learn.microsoft.com/en-us/azure/governance/machine-configuration/overview) is an extension of Azure Policy that seems to do broadly the same job as DSC, but with more native integration to the Azure platform.

- [Terraform Export from the Azure Portal (Public Preview)](https://techcommunity.microsoft.com/blog/azuretoolsblog/announcing-public-preview-of-terraform-export-from-the-azure-portal/4409889) : Alongside ARM templates and Bicep, you can now [export your resources from the Azure portal](https://learn.microsoft.com/en-gb/azure/developer/terraform/azure-export-for-terraform/get-started-export-resources-portal?tabs=azure-cli) as Terraform configuration files. Code can be generated for both the AzureRM and AzAPI providers. The feature is enabled via a new [Microsoft.AzureTerraform resource provider](https://learn.microsoft.com/en-gb/azure/developer/terraform/azure-export-for-terraform/resource-provider-overview).





