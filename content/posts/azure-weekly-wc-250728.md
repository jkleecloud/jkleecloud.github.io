+++
title = 'Azure Snippets w/c 28/07/2025'
date = 2025-08-01T08:00:16+01:00
draft = false
categories = ['Azure Weekly 2025']
tags = ['Azure Backup', 'DB for PostgreSQL', 'Azure DNS', 'Azure Firewall', 'AKS', 'Azure Storage', 'Compute', 'Cosmos DB', 'Defender for Cloud', 'Identity', 'IaC']
+++

Summary of Azure snippets for the week commencing 28th July 2025, grouped by Azure service. No major announcements since my last post, but there have been a number of smaller ones of interest to users of specific services.

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [Azure Backup](#azure-backup)
- [Azure DB for PostgreSQL](#azure-database-for-postgresql)
- [Azure DNS](#azure-dns)
- [Azure Firewall](#azure-firewall)
- [Azure Kubernetes Services](#azure-kubernetes-services)
- [Azure Storage](#azure-storage)
- [Compute](#compute)
- [Cosmos DB](#cosmos-db)
- [Defender for Cloud](#defender-for-cloud)
- [Identity](#identity)
- [Infrastructure as Code](#infrastructure-as-code)

## Azure Backup

- [Azure Backup standard policies support for Trusted Launch virtual Machines (GA)](https://azure.microsoft.com/en-gb/updates?id=498439) : Trusted Launch support with standard backup policies enables seamless backup configuration for secure VMs, aligning with Trusted Launch becoming the default across VM creation interfaces. Previously you had to create new enhanced backup policies to back up Trusted Launch VMs, so this removes a potential point of friction in moving to Trusted Launch VMs.

- [Migrate Azure VM backups from standard to enhanced policy (GA)](https://azure.microsoft.com/en-gb/updates?id=497155) : But if you do want to move to enhanced policies, it's now easier to do so :-) Azure Backup now supports migration to the enhanced policy for Azure VM backups using standard policy. The migration of VM backups to enhanced policy also allows you to migrate your VMs to Trusted Launch (though this is less of an issue now given the item above) and use Premium SSD v2 and Ultra Disks for the VMs without disrupting the existing backups.

- [Agentless multi-disk crash-consistent backup for Azure VMs (GA)](https://azure.microsoft.com/en-gb/updates?id=499192) : [Agentless multi-disk crash consistent backups for Azure VM](https://learn.microsoft.com/en-us/azure/backup/backup-azure-vms-agentless-multi-disk-crash-consistent) allows you to take VM backups without installing additional software like the VM agent or snapshot extension in your VM. If your workload is performance sensitive and can recover from crash consistent backups, this feature can help reduce the quiesce time during backup. You can also use this feature if your operating system is not supported for application or file-system consistent backup.

## Azure Database for PostgreSQL

- [Azure Database for PostgreSQL Entra authentication for Power BI Desktop (GA)](https://azure.microsoft.com/en-gb/updates?id=498175) : You can now use Microsoft Entra ID authentication to [connect to Azure Database for PostgreSQL from Power BI Desktop](https://learn.microsoft.com/en-gb/power-query/connectors/postgresql). This update simplifies access management, enhances security, and helps you support your organization’s broader Entra-based authentication strategy.

## Azure DNS

- [Azure DNS security policy (GA)](https://azure.microsoft.com/en-gb/updates?id=497535) : [DNS security policy](https://learn.microsoft.com/en-us/azure/dns/dns-security-policy) offers the ability to filter and log DNS queries at the virtual network (VNet) level. Policy applies to both public and private DNS traffic within a VNet. DNS logs can be sent to a storage account, log analytics workspace, or event hubs. You can choose to allow, alert, or block DNS queries.

## Azure Firewall

- [Customer controlled maintenance for Azure Firewall (GA)](https://azure.microsoft.com/en-gb/updates?id=497160) : Azure Firewall enables users to set a [maintenance window](https://learn.microsoft.com/en-us/azure/firewall/customer-controlled-maintenance?tabs=portal) with a minimum duration of 5 hours, recurring daily, to best accommodate their requirements and minimize unexpected downtime. Firewalls with an associated maintenance configuration will not undergo upgrades outside the designated maintenance period. Customers can now set maintenance windows for outside working hours, for example.

## Azure Kubernetes Services

- [AKS Release 2025-07-20 now available (GA)](https://github.com/Azure/AKS/releases/tag/2025-07-20) : Few things to note from this release:
    - Kubernetes 1.27 LTS version and 1.30 community version are going out of support by July 30th
    - Kubernetes v1.33 is now eligible for Long-Term Support
    - [Virtual Machines (VM) node pools](https://learn.microsoft.com/en-gb/azure/aks/virtual-machines-node-pools) are now enabled by default when creating a new node pool. Previously Virtual Machine Scale Sets (VMSS) were the default node pool type when creating a node pool in AKS.
    - [Kubelet Service Certificate Rotation](https://learn.microsoft.com/en-gb/azure/aks/certificate-rotation) will begin rollout to all remaining public regions, starting on 23 July
    - [Static Block allocation mode](https://learn.microsoft.com/en-gb/azure/aks/configure-azure-cni-static-block-allocation) for Azure CNI Networking is now Generally Available (improves scalability for large clusters). Note that you can't expose an application behind a Private Link Service using a Kubernetes load balancer if you use static block allocation.

- [Virtual Machines node pools support (GA)](https://azure.microsoft.com/en-gb/updates?id=498258) : [Virtual Machines node pools](https://learn.microsoft.com/en-gb/azure/aks/virtual-machines-node-pools) support in AKS is now generally available. With Virtual Machines node pools, Azure Kubernetes Services directly manages the provisioning and bootstrapping of every single node. When deploying a workload onto AKS, each node pool typically can only contain one virtual machine (VM) type or SKU. Virtual Machines node pools allow the capability to add multiple VM SKUs of a similar family to a single node pool. (As mentioned above, this will be the default node pool creation type in AKS going forward.)

- [Azure CNI static block allocation for pod subnet (GA)](https://azure.microsoft.com/en-gb/updates?id=498166) : [Azure CNI Pod Subnet - Static Block Allocation](https://learn.microsoft.com/en-us/azure/aks/configure-azure-cni-static-block-allocation) enables VNET routed IP addresses that can scale to over 1M pods, providing the simplicity and low latency of a flat network. Each node receives pre-allocated CIDR blocks, and all pods on that node obtain IP addresses from these ranges. This approach delivers massive scale, previously only available with overlay networks, while maintaining all the benefits of a flat network architecture. It also works seamlessly alongside existing dynamic IP allocation for pod subnet – simply deploy it on new node pools with dedicated subnets.

- [Web Application Firewall (WAF) running on Application Gateway for Containers (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=498272) : With the addition of [Azure WAF support](https://learn.microsoft.com/en-us/azure/application-gateway/for-containers/web-application-firewall), Application Gateway for Containers workloads can now protect workloads from web-based attacks like SQL injections, cross-site scripting, protocol anomalies, and more. Brings AGIC functionality further in line with 'standard' App Gateways.

- [Node auto-provisioning support in AKS (GA)](https://azure.microsoft.com/en-gb/updates?id=498247) : Managing dynamic workloads in Kubernetes can often lead to overprovisioning, idle resources, and additional operational overhead from maintaining pre-configured node pools. To address this, [Node Auto-Provisioning (NAP) support in AKS](https://learn.microsoft.com/en-gb/azure/aks/node-autoprovision?tabs=azure-cli) is now generally available. NAP automatically provisions single-instance nodes (VMs) in response to unscheduled pods, eliminating the need for pre-configured node pools. It uses pending pod resource requirements to decide the optimal virtual machine configuration to run those workloads in the most efficient and cost-effective manner. Based on [Karpenter](https://karpenter.sh/) (open-source).

 - [Cluster Extension Manager move to AKS control plane (GA)](https://azure.microsoft.com/en-gb/updates?id=498242) : Extension Manager, the core component responsible for managing the lifecycle of AKS cluster extensions, has been moved from customer worker nodes to the AKS control plane. This transition enhances security, simplifies networking, and reduces operational overhead - delivering a more robust and streamlined experience for managing [extensions](https://learn.microsoft.com/en-us/azure/aks/cluster-extensions) like Azure Backup, Azure Container Storage, Flux (GitOps)  as well as third-party solutions such as Cast AI and Cilium.

## Azure Storage

- [Log or block shared access signature (SAS) tokens for Azure Storage based on expiration policy (GA)](https://azure.microsoft.com/en-gb/updates?id=498759) : [SAS expiration actions](https://learn.microsoft.com/en-us/azure/storage/common/sas-expiration-policy?tabs=azure-portal#define-the-sas-expiration-action) allow you to configure actions for using a SAS token that doesn’t adhere to the defined SAS expiration policy: do you want to log the event, or block the request entirely? Auditing with ‘Log’ action helps you detect trends and investigate access without disrupting workflows, while ‘Block’ action lets you enforce zero-tolerance for out-of-policy SAS tokens.

## Compute

- [Trusted launch default for new Gen2 VMs & Scale Sets (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=497388) : [Trusted Launch will soon be the default](https://learn.microsoft.com/en-gb/azure/virtual-machines/trusted-launch#preview-trusted-launch-as-default) for new deployments of Gen2 Virtual Machines (VMs), Virtual Machine Scale Sets (Scale set) and Azure Compute Gallery (ACG) resources. This will help enhance the foundational security of new Azure Gen2 VMs & Scale set deployments without any change to existing deployment scripts. Currently need to register the preview feature to support this; and it does have a bug whereby you can't select Standard security for VMs deployed via the portal once the preview feature is registered. MS say this will be fixed for GA.

## Cosmos DB

- [Cosmos DB in Microsoft Fabric (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=498185) : This was initially announced at Build in limited preview, but is now publically available, including new features. [Cosmos DB in Fabric](https://blog.fabric.microsoft.com/en-us/blog/announcing-cosmos-db-in-microsoft-fabric-preview-with-exciting-new-features?ft=All) brings the power of Azure Cosmos DB to the Fabric platform — combining high availability, dynamic scaling, and AI-optimized performance in a fully managed experience. Cosmos DB in Fabric is powered by the same Azure Cosmos DB service, now natively integrated into Fabric.

## Defender for Cloud

- [Helm support for container security with Microsoft Defender for Cloud](https://techcommunity.microsoft.com/t5/microsoft-defender-for-cloud/your-cluster-your-rules-helm-support-for-container-security-with/ba-p/4433842) : The Microsoft Defender for Containers sensor can now be installed on AKS, EKS (Amazon AWS), and GKE (Google Cloud) clusters [using Helm](https://learn.microsoft.com/en-us/azure/defender-for-cloud/deploy-helm). Previously required an AKS add-on, or Arc on-boarding for other cloud providers.

 - [Defender for Storage: Malware Scan Error Message Update (GA)](https://techcommunity.microsoft.com/t5/microsoft-defender-for-cloud/defender-for-storage-malware-scan-error-message-update/ba-p/4436304) : This is a bit niche but matters if your automation for Defender for Storage alerts (e.g. to remove flagged malware) relies on the current error message format to handle errors. Starting August 2025, Defender for Storage will update the format of [error messages](https://learn.microsoft.com/en-us/azure/defender-for-cloud/understand-malware-scan-results#error-states) returned by malware scanning - update any workflows that rely on the old format.

## Identity

- [Microsoft Entra: Cross-cloud synchronization (Public Preview)](https://techcommunity.microsoft.com/blog/microsoft-entra-blog/streamline-user-management-across-microsoft-clouds/4422536) : A bit outside the realm of my usual posts, but I thought it was interesting since it touches on Azure resource management. [Cross-cloud sync](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/cross-tenant-synchronization-configure?pivots=cross-cloud-synchronization) enables automated user lifecycle management across Microsoft commercial, US Government, and China clouds. It is off by default, requires explicit admin enablement, a Microsoft Entra ID Governance license, and supports configuration via portal, PowerShell, and Graph API.

## Infrastructure as Code

- [Bicep templates support for Microsoft Entra ID resources (GA)](https://techcommunity.microsoft.com/blog/azuregovernanceandmanagementblog/announcing-ga-of-bicep-templates-support-for-microsoft-entra-id-resources/4437163) : You can now create [Bicep templates](https://learn.microsoft.com/en-us/graph/templates/bicep/) to deploy Entra ID resources such as groups, applications and security principals (e.g. users or service accounts) using Microsoft Graph, supported by the Microsoft Graph for Bicep extension. Entra ID resources can now be created as part of your Azure IaC deployments, rather than having to be done separately using Graph PowerShell. This is a powerful update to widen the scope of resources that can be created using Bicep - and since this is an extension for Microsoft Graph (with Entra ID resources being the first supported), support for other Graph resources may come in in the future. (Terraform also has a [resource provider](https://registry.terraform.io/providers/hashicorp/azuread/latest) that can manage Entra ID resources - interestingly though, while the provider is up-to-date, they haven't updated its name and still refer to it as Azure AD!)

- [Azure CLI and Azure PowerShell updates from Build](https://techcommunity.microsoft.com/t5/azure-tools-blog/azure-cli-and-azure-powershell-build-2025-announcement/ba-p/4415515) : One final item from Build that I hadn't covered previously - updates to Azure CLI and Azure PowerShell include:
    - Long Term Support versions for CLI and PowerShell - more stability if you're worried about breaking changes
    - PowerShell moving to use SecureString for all keys, tokens and secrets - this is a breaking change
    - PowerShell UI enhancements including progress bars, smarter output formatting and accepting JSON inputs
    - Enhancements to Copilot in Azure integration (there's always an AI angle these days :-)
    
