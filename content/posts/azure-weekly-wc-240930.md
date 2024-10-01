+++
title = 'Azure Snippets w/c 30/09/2024'
date = 2024-10-04T08:00:16+01:00
draft = true
categories = ['Azure Weekly 2024']
tags = ['DB for PostgreSQL', 'Redis', 'IaC', 'NSG', 'Application Gateway']
+++

Summary of Azure snippets for the week commencing 30th September 2024, grouped by Azure service. Almost back to normal posting cadence :-)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [Application Gateway](#application-gateway)
- [Azure Cache for Redis](#azure-cache-for-redis)
- [Azure DB for PostgreSQL](#azure-db-for-postgresql)
- [Azure Kubernetes Service](#azure-kubernetes-service)
- [Infrastructure as Code](#infrastructure-as-code)
- [Network Security Groups](#network-security-groups)

## Application Gateway

- [Azure Application Gateway support for TLS 1.0 and TLS 1.1 will end by 31 August 2025 (RET)](https://azure.microsoft.com/en-us/updates/v2/Azure-Application-Gateway-support-for-TLS-10-and-TLS-11-will-end-by-31-August-2025) : All connections (frontend and backend) to Application Gateway must use Transport Layer Security (TLS) 1.2 or later, as support for TLS 1.0 and 1.1 on Azure Application Gateway will be discontinued starting 31st August 2025.

## Azure Cache for Redis

- [Smaller Enterprise tier cache instance for Azure Cache for Redis (GA)](https://azure.microsoft.com/en-us/updates/v2/Smaller-Enterprise-tier-cache-instance-for-Azure-Cache-for-Redis) : Following the very pricy Large Enterprise instances, there's now a more cost-effective smaller one. Runs on burstables and recommended for dev/test only, but [very much cheaper](https://azure.microsoft.com/en-gb/pricing/details/cache/) than the other Enterprise tiers.

## Azure DB for PostgreSQL

- [Online migration from Azure Database for PostgreSQL - Single Server to Flexible Server (GA)](https://azure.microsoft.com/en-us/updates/v2/Online-migration-from-Azure-Database-for-PostgreSQL-Single-Server-to-Flexible-Server) : Now out of preview, [minimal downtime migration](https://learn.microsoft.com/en-us/azure/postgresql/migrate/migration-service/tutorial-migration-service-single-to-flexible?tabs=portal%2Conline) for PostgreSQL Single Server instances.

## Azure Kubernetes Service

- [gRPC and frontend mTLS now available for Application Gateway for Containers (GA)](https://azure.microsoft.com/en-us/updates/v2/grpc-and-frontend-mutual-authentication-available-on-application-gateway-for-containers) : Application Gateway for Containers now supports [gRPC](https://learn.microsoft.com/en-us/azure/application-gateway/for-containers/grpc) and frontend mutual authentication ([mTLS](https://learn.microsoft.com/en-us/azure/application-gateway/for-containers/how-to-frontend-mtls-gateway-api?tabs=alb-managed)).  With both frontend and backend mutual authentication, end-to-end mutual authentication is now possible. This fills what I considered a fairly significant gap in the functionality of App Gateway for Containers, and brings it more in line with other ingress/gateway solutions.
- [Long-term support for Kubernetes version 1.27 and 1.30 in AKS (GA)](https://azure.microsoft.com/en-us/updates/v2/Long-term-support-for-version-1-27-and-1-30-in-AKS) : K8s v1.30 has now joined 1.27 on the AKS [LTS](https://learn.microsoft.com/en-us/azure/aks/long-term-support) list.
- [Open Service Mesh add-on for AKS will be retired on September 30, 2027 (RET)](https://azure.microsoft.com/en-us/updates/v2/Open-Service-Mesh-add-on-for-AKS-will-be-retired-on-September-30-2027) : Istio is (currently) the only option for a 'native' AKS service mesh add-on going forward.
- [Virtual machines node pools support in AKS (Public Preview)](https://azure.microsoft.com/en-us/updates/v2/Virtual-machines-node-pools-support-in-AKS) : With [virtual machines node pools](https://learn.microsoft.com/en-gb/azure/aks/virtual-machines-node-pools), Azure Kubernetes Service directly manages the provisioning and bootstrapping of every single node. (For Virtual Machine Scale Sets node pools, AKS manages the model of the Virtual Machine Scale Sets and uses it to achieve consistency across all nodes in the node pool.) Virtual Machines node pools allow the capability to add multiple VM SKUs of a similar family (e.g. different D-series SKUs) to a single node pool.
- [Latest AKS release (GA)](https://github.com/Azure/AKS/releases/tag/2024-09-18) : Some ongoing updates from the last release, plus 1.30 in LTS (see above), and AKS patch versions 1.28.13, 1.29.8, 1.30.4 are now available

## Infrastructure as Code

- [Transition from Helm Repositories to OCI Artifacts for Storing Helm Charts (RET)](https://azure.microsoft.com/en-us/updates/v2/acr-helm-repositories-retirement) : Starting March 30th, 2025, Azure Container Registry will no longer support Helm v2. Therefore, the legacy “Helm repositories” functionality will also be retired. After this date, Azure Container Registry will only support storing Helm charts as Open Container Initiative (OCI) Artifacts. Get your migration sorted out where needed - any Helm charts not stored as OCI Artifacts in ACR will be deleted after 30th March 2025!

## Network Security Groups

- [Network security group flow logs in Azure Network Watcher will be retired (RET)](https://azure.microsoft.com/en-us/updates/v2/Azure-NSG-flow-logs-Retirement) : Flow logs to be retired on 30/9/27, but you won't be able to create new ones from 30/6/25. Migration path is to [virtual network flow logs](https://learn.microsoft.com/en-gb/azure/network-watcher/vnet-flow-logs-portal), and a [migration process](https://learn.microsoft.com/en-gb/azure/network-watcher/nsg-flow-logs-migrate) is available.