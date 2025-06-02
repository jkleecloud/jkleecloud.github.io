+++
title = 'Azure Snippets w/c 26/05/2025'
date = 2025-06-02T08:00:16+01:00
draft = true
categories = ['Azure Weekly 2025']
tags = ['API Center', 'APIM', 'AKS', 'Networking']
+++

Summary of Azure snippets for the week commencing 26th May 2025, grouped by Azure service.

With Build taking place last week, a lot of announcements have dropped as usual. The [Build 2025 Book of News](https://news.microsoft.com/build-2025-book-of-news/) has all the details of announcements from there. Plenty of AI focus as usual - I'll cover some of the stuff that isn't AI-related here :-)

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [API Center](#api-center)
- [API Management](#api-management)
- [Azure Kubernetes Services](#azure-kubernetes-services)
- [Networking](#networking)

## API Center

- [New Free Tier (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=492168) : This one's probably not surprising as API Center is extremely expensive if you're not at the large enterprise scale it assumes. The [Free plan is much more limited](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/azure-subscription-service-limits?toc=%2Fazure%2Fapi-center%2Ftoc.json&bc=%2Fazure%2Fapi-center%2Fbreadcrumb%2Ftoc.json#azure-api-center-limits) than Standard, which also isn't surprising!

## API Management

- [Premium v2 Tier for Azure API Management (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=492158) : APIM v2 tiers continue to expand with a [Premium v2 tier](https://techcommunity.microsoft.com/blog/integrationsonazureblog/announcing-the-open-public-preview-of-the-premium-v2-tier-of-azure-api-managemen/4415359) joining Basic and Standard. The API Management v2 tiers (SKUs) are built on a new, more reliable and scalable platform and are designed to make API Management accessible to a broader set of customers and offer flexible options for a wider variety of scenarios. Main update for Premium v2 seems to be a new and improved VNet injection model. Currently available only in 6 regions (including UK South).

- [Model Context Protocol support in Azure API Management and Azure API Center (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=491990) : MCP is an open standard to enable connections between AI models and external tools and systems, so its introduction into APIM could be significant for developing AI-enabled APIs.

- [Applications in Azure API Management (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=492163) : Register APIs as Entra ID applications directly from APIM, and those APIs can be protected by Entra ID and use OAuth 2.0 to authenticate access. Enabled by APIM's new support for built-in OAuth 2.0 application-based access to product APIs using the client credentials flow. With [Applications](https://techcommunity.microsoft.com/blog/integrationsonazureblog/announcing-the-public-preview-of-the-applications-feature-in-azure-api-managemen/4415777), API publishers and developers can now more effectively manage client identity, access, and authorisation flows.

- [Inbound Private Endpoint Support for Azure API Management Standard v2 (GA)](https://azure.microsoft.com/en-gb/updates?id=492607) : This brings the Standard v2 tier in line with the 'classic' Standard tier in terms of protecting the Gateway behind a Private Endpoint.

## Azure Kubernetes Services

- [AKS Release 2025-05-19 now available (GA)](https://github.com/Azure/AKS/releases/tag/2025-05-19) : Among other new features, Kubernetes 1.31 and 1.32 are now designated as LTS, and Kubernetes 1.33 is available in preview.

- [Every AKS version is now long term support (LTS) compatible (GA)](https://azure.microsoft.com/en-gb/updates?id=492579) : This is a big one for those who can't upgrade AKS on the community support release cadence - AKS will now ensure that every community version released (GA) is compatible with long term support (LTS), starting with version 1.28 LTS from April 2025. Versions 1.27, 1.28, 1.29, and 1.30 are now LTS, with 1.31 and 1.32 in the 19th May release (see above). Check out the [release calendar](https://learn.microsoft.com/en-us/azure/aks/supported-kubernetes-versions?tabs=azure-cli) in the docs to see the lifecycle timelines for each K8s version in AKS from 1.27 onwards.

## Networking

- [Private Subnet (GA)](https://azure.microsoft.com/en-gb/updates?id=492953) : Essentially, this removes the 'implicit' [default outbound connectivity](https://learn.microsoft.com/en-us/azure/virtual-network/ip-services/default-outbound-access) to the Internet that e.g. VMs have when created in a network without an 'explicit' outbound connection mechanism, which is through default public IP addresses that aren't very visible. With a private subnet, you'll need to explicitly create an outbound connectivity method, such as a NAT Gateway or Public IP address. Important to note that this will be the default deployment mode for all new VNets/subnets after 30th September 2025. (NAT Gateways and Public IP addresses, of course, are not free :-)

- [VM Network Troubleshooter (Public Preview)](https://azure.microsoft.com/en-gb/updates?id=491437) : Customers can identify blocked ports faster with the Azure Portal's latest enhancement. The VM Overview blade in the Azure Portal has a new [troubleshooter tool](https://learn.microsoft.com/en-gb/azure/network-watcher/vm-network-troubleshooter) allowing users to run network diagnostics and check for common ports (HTTP/S and RDP at the moment) being blocked. Anyone who's had to troubleshoot VM connectivity will most likely appreciate anything that makes it easier!
