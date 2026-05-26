+++
title = 'Azure Snippets w/c 25/05/2026'
date = 2026-05-26T08:00:16+01:00
draft = true
categories = ['Azure Weekly 2026']
tags = ['DB for PostgreSQL', 'Redis', 'IaC', 'NSG', 'Application Gateway', 'Azure Backup', 'Virtual Network Manager', 'Compute', 'FinOps', 'Azure Storage']
+++

Summary of Azure snippets for the week commencing 25th May 2026, grouped by Azure service.

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

## Azure Backup

- [Bulk Restore for Azure Virtual Machines using Azure Backup (Public Preview)](https://azure.microsoft.com/en-us/updates?id=561373) : Enables customers to [restore multiple VMs](https://learn.microsoft.com/en-us/azure/backup/backup-azure-arm-restore-vms#restore-vms-in-bulk-preview) (up to 100) in a single operation. During large-scale outages or ransomware incidents, you can use bulk VM restore to orchestrate restore of multiple VMs as one coordinated operation that simplifies recovery at-scale. Each VM restore runs separately, and you can track its progress independently while retaining full VM-level flexibility and control.

## Azure Kubernetes Services

- [AKS Release 2026-04-28 now available (GA)](https://github.com/Azure/AKS/releases/tag/2026-04-28) : The main item to call out in this release is a mitigation for the Linux privilege escalation vulnerabilities referred to as Copy Fail, DirtyFrag and Fragnesia, which can allow an unprivileged pod to escalate to root on the underlying node. Make sure your node pools are updated - check the [AKS security bulletin](https://learn.microsoft.com/en-gb/azure/aks/security-bulletins/overview?tabs=aks-addons%2Caks-node-image%2Caks-cluster#aks-2026-0003-aks-advisory--mitigation-guide-for-cve-2026-31431-copy-fail) and the [advisory and mitigation guide](https://github.com/Azure/AKS/issues/5753). There are a number of other updates as well - check out the release notes for details.

## Azure Storage

- [Entra-only identities with Azure Files (GA)](https://azure.microsoft.com/en-us/updates?id=562359) : Securely access file shares using cloud-native identities without requiring Active Directory or hybrid identity infrastructure. With Microsoft Entra ID as the authentication authority, users can access Azure Files using [Kerberos-based authentication](https://learn.microsoft.com/en-us/azure/storage/files/storage-files-identity-auth-hybrid-identities-enable?tabs=azure-portal%2Cintune#enable-cloud-only-groups-support-mandatory-for-cloud-only-identities) backed entirely by cloud identities - eliminating dependency on domain controllers and simplifying storage and identity architecture. Been a while coming, this one - it'll be useful to be able to go fully cloud-native for Azure Files access.

## Virtual Networks

- [Azure Virtual Network updates – default limits increased for NSGs and route tables (GA)](https://azure.microsoft.com/en-us/updates?id=562695) : The new defaults are now 2,000 security rules per NSG, 6,000 addresses or ports per NSG rule, 1,000 routes per route table, and 600 route tables per subscription. Given the ever-increasing size and complexity of Azure Virtual Network infrastructures, and the number of rules and routes needed in a complex secure setup, this update is likely to be welcome.

- [Network Watcher rule impact analyser (GA)](https://azure.microsoft.com/en-gb/updates?id=562690) : [Assess the potential impact](https://learn.microsoft.com/en-gb/azure/network-watcher/traffic-analytics-rule-impact-analyzer) of your network security group (NSG) or security admin rule changes on live network traffic before applying them. This feature is accessible through the Azure portal and leverages Azure Network Watcher traffic analytics and virtual network flow logs to deliver data-driven visibility into how NSG or network manager rule updates could influence your current network behavior. 

## Virtual Network Manager

- [Azure Virtual Network Manager rule impact analyzer (GA)](https://azure.microsoft.com/en-gb/updates?id=562010) : Similar to the Network Watcher update, but part of VNM for security admin rules. [Simulate the impact of your security admin rules](https://learn.microsoft.com/en-us/azure/virtual-network-manager/how-to-simulate-security-admin-rules) on your virtual networks before deploying your rules. This feature is available in the Azure portal and is powered by Azure Network Watcher traffic analytics and virtual network flow logs, providing data-driven insights into how security admin rule deployments could affect your existing virtual network traffic.


