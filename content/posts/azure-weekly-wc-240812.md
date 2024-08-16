+++
title = 'Azure Snippets w/c 12/08/2024'
date = 2024-08-16T08:00:16+01:00
draft = false
categories = ['Azure Weekly 2024']
tags = ['DB for PostgreSQL', 'AKS', 'Azure Portal', 'Entra ID']
+++

Summary of Azure snippets for the week commencing 12th August 2024, grouped by Azure service.

GA = Generally Available  
Public/Private Preview = as stated :-)

Azure services with highlighted updates this week:

- [Azure DB for PostgreSQL](#azure-db-for-postgresql)
- [Azure Kubernetes Service](#azure-kubernetes-service)
- [Azure Portal/Entra ID](#azure-portalentra-id)

## Azure DB for PostgreSQL

- [Terraform support for geo-restore in Azure Database for PostgreSQL - Flexible Server (GA)](https://azure.microsoft.com/en-us/updates/v2/Terraform-support-for-geo-restore-in-Azure-Database-for-PostgreSQL-Flexible-Server) : You can now use [Terraform](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/postgresql_flexible_server) to perform geo-restore for Azure Database for PostgreSQL - Flexible Server data.

## Azure Kubernetes Service

- [Azure CNI Powered by Cilium & Azure CNI Overlay support in AKS (Public Preview)](https://azure.microsoft.com/en-us/updates/v2/CNI-Powered-by-Cilium-Azure-CNI-Overlay-support-AKS) : Public preview of Azure CNI Overlay dual-stack with [Azure CNI powered by Cilium](https://learn.microsoft.com/en-gb/azure/aks/azure-cni-powered-by-cilium) for Linux clusters in AKS is now available. This enhancement enables AKS clusters to support IPv4 and IPv6 network policies, providing greater flexibility and control over network traffic within your Kubernetes environments. 

## Azure Portal/Entra ID

- [Enable multifactor authentication for your tenant by 15 October 2024 (GA)](https://azure.microsoft.com/en-us/updates/v2/Enable-multifactor-authentication-for-your-tenant-by-15-October-2024) : This has been on the way for a little while - starting 15 October 2024, MS will require users to use multifactor authentication (MFA) to sign into the Azure portal, Microsoft Entra admin center, and Intune admin center. Applies to break-glass accounts as well - check the [documentation](https://learn.microsoft.com/en-gb/entra/identity/authentication/concept-mandatory-multifactor-authentication) for more info.
