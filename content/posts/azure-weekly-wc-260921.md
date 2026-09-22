+++
title = 'Azure Snippets w/c 21/09/2026'
date = 2026-09-22T08:00:16+01:00
draft = false
categories = ['Azure Weekly 2026']
tags = ['Azure Functions', 'AKS', 'AI', 'Foundry', 'Virtual Networks', 'Compute']
+++

Summary of Azure snippets for the week commencing 21st September 2026, grouped by Azure service.

Can't believe it's been almost 3 months since my last post!

For all the updates on Azure platform resources and products - [Azure updates from Microsoft](https://azure.microsoft.com/updates/)

GA = Generally Available  
Public/Private Preview = as stated  
RET = Service retirement

Azure services with highlighted updates this week:

- [Azure Functions](#azure-functions)
- [Azure Kubernetes Services](#azure-kubernetes-services)
- [Compute](#compute)
- [Microsoft Foundry / AI](#microsoft-foundry--ai)
- [Virtual Networks](#virtual-networks)

## Azure Functions

- [TLS/SSL certificate and end-to-end TLS encryption support for Azure Functions Flex Consumption (GA)](https://azure.microsoft.com/en-us/updates?id=570940) : Azure Functions Flex Consumption support for TLS/SSL certificates is now generally available through a new site-scoped certificate model. Each function app can hold up to 3 private (.pfx) and 3 public (.cer) certificates uploaded directly, imported from Azure Key Vault, or issued as free App Service Managed Certificates to enable custom domains, client-certificate authentication, and mutual TLS scenarios on Flex Consumption. End-to-end TLS encryption is also generally available for Flex Consumption and allows traffic encryption between the platform front ends and the workers that run your functions. Removes a previous impediment to using Flex Consumption plans!

## Azure Kubernetes Services

- [AKS Release 2026-09-04 now available (GA)](https://github.com/Azure/AKS/releases/tag/2026-09-04) : Kubernetes 1.37 Preview is being rolled out, patch versions 1.36.3, 1.35.7, and 1.34.10 are now available; and among the preview features is a [Cluster Health Monitor](https://learn.microsoft.com/en-gb/azure/aks/cluster-health-monitor) which looks worth checking out to augment your cluster monitoring.

- [Connect to AKS clusters using Azure Bastion (GA)](https://azure.microsoft.com/en-us/updates?id=570030) : Customers can [establish a secure tunnel from their local machine through Azure Bastion](https://learn.microsoft.com/en-us/azure/bastion/bastion-connect-to-aks-private-cluster) to an AKS cluster API server. The integration enables customers to use standard Kubernetes tools while avoiding public exposure of private cluster endpoints. It reduces the need to deploy and maintain separate jump boxes, VPN servers, or additional access agents.

- [Artifact Streaming (GA)](https://azure.microsoft.com/en-gb/updates?id=570095) : [Artifact streaming](https://learn.microsoft.com/en-gb/azure/aks/artifact-streaming-overview) will allow you to scale your workloads without having to fully wait for images to be pulled into the clusters. Artifact Streaming streams container images from ACR to AKS, so you only pull the necessary layers for the initial pod startup. This feature reduces the time it takes to deploy your workloads.

- [Control plane metrics collection for AKS with Managed Prometheus (GA)](https://azure.microsoft.com/en-us/updates?id=568830) : This capability gives AKS customers [native observability](https://learn.microsoft.com/en-gb/azure/aks/control-plane-metrics-monitor) into key managed control plane components, including the API server, etcd, kube-scheduler, kube-controller-manager, cluster autoscaler, and node auto-provisioning. Only works with Managed Prometheus at present, and there are some other limitations to check.

- [Prepared Image Specification (Public Preview)](https://azure.microsoft.com/en-us/updates?id=567949) : With AKS [Prepared Image Specification](https://learn.microsoft.com/en-gb/azure/aks/prepared-image-specification-overview), customers can create preconfigured node images that include required container images and customizations ahead of time, enabling new nodes to start in a ready-to-run state. This helps workloads achieve faster and more predictable scaling, reduce application startup latency, and improve operational efficiency during growth and burst traffic events. Another performance boost for AKS workloads alongside artifact streaming.

## Compute

- [Per-disk resiliency for Azure VMs (Public Preview)](https://azure.microsoft.com/en-us/updates?id=569711) : [Per-disk resiliency](https://learn.microsoft.com/en-gb/azure/virtual-machines/disks-per-disk-resiliency) provides another option for applications that can tolerate the temporary loss of an individual data disk. When enabled, Azure detaches and takes only the affected disk offline while the VM and its remaining disks continue running. Once disk connectivity is restored, Azure automatically attaches and brings the disk back online. Examples of use: Production VMs with backup or auxiliary disks, so a secondary disk issue does not interrupt the primary workload; clustered and shared-disk applications with their own high-availability or failover logic; containerized workloads with per-pod disks, so one persistent volume can recover without disrupting other pods on the node. This last potential use case is interesting for containerised apps. Preview is in limited regions, but unusually they include both UK South and UK West!

## Microsoft Foundry / AI

- [Enable and disable controls for Microsoft Foundry agents in Agent 365 (GA)](https://azure.microsoft.com/en-us/updates?id=571826) : Microsoft Foundry now exposes enable and disable actions for Foundry agent objects within the Agent 365 governance surface in Microsoft Admin Center. This fills a core governance gap by bringing Foundry agents into the Admin Center alongside other agent types, so IT and governance teams manage the full agent estate consistently and can meet compliance and security requirements around which agents are active.

- [Network egress controls for hosted agents (Public Preview)](https://azure.microsoft.com/en-us/updates?id=571821) : Microsoft Foundry now lets customers govern the outbound connections a hosted agent can make. Rules live in the agent's Responsible AI policy and are enforced inside the Foundry-managed agent sandbox before traffic leaves the runtime, so no separate network appliance is required for basic allow-listing. Definitely a control worth implementing when developing agents!

- [Publishing Microsoft Foundry agents to Microsoft 365 Copilot and Teams (GA)](https://azure.microsoft.com/en-us/updates?id=571816) : Foundry developers previously had no native path to make their agents operational across Microsoft 365, requiring separate deployment pipelines, bot registrations, and app manifests. With this release you publish an agent directly into Microsoft 365 Copilot and [Teams](https://learn.microsoft.com/en-gb/azure/foundry/agents/how-to/agent-365), where it becomes discoverable to end users in the surfaces where they already work. Published agents remain governed through the same Microsoft Entra and Agent 365 controls IT uses for the rest of the organization, so distribution does not mean giving up governance. This seemed a bit of a gap in Foundry's capabilities, and something that's come up in discussions I've had, so seems like a good update for agent development.

- [Azure SRE Agent VNet Integration (GA)](https://azure.microsoft.com/en-gb/updates?id=569695) : [VNet integration](https://techcommunity.microsoft.com/blog/appsonazureblog/azure-sre-agent-vnet-integration-is-now-generally-available/4549774) enables Azure SRE Agent to operate within your existing network controls, including Network Security Groups (NSGs), private DNS, and firewall policies, etc. With VNet support, the agent can securely access private resources, including services behind private endpoints, during incident investigation and remediation without requiring changes to your network boundary. This capability helps organizations extend Azure SRE Agent into security-sensitive environments while maintaining existing networking, security, and compliance controls. Follows the same pattern as other services, working within a dedicated (delegated) subnet.

- [Live Reports for Azure SRE Agent (Public Preview)](https://azure.microsoft.com/en-us/updates?id=569690) : [Live Reports](https://techcommunity.microsoft.com/blog/appsonazureblog/azure-sre-agent-introducing-live-reports/4549732) help operations teams create dynamic operational views directly from SRE Agent conversations and keep them continuously up to date with the latest data from connected environments. You describe a dashboard in chat; the agent builds it, and it refreshes every time you open it.

## Virtual Networks

- [Azure Multicloud Interconnect (Public Preview)](https://azure.microsoft.com/en-us/updates?id=570364) : A managed service that provides [private connectivity between Azure and supported cloud providers](https://learn.microsoft.com/en-gb/azure/multicloud-interconnect/overview), with Amazon Web Services (AWS) available as the first supported provider in preview. With [Azure Multicloud Interconnect](https://azure.microsoft.com/en-us/blog/introducing-azure-multicloud-interconnect-for-aws/), you can [deploy a multicloud connection](https://techcommunity.microsoft.com/blog/azurenetworkingblog/simpler-private-connectivity-between-azure-and-aws-with-azure-multicloud-interco/4550556) directly from the Azure portal, select your cloud provider, region, and bandwidth, and onboard your environment through a guided experience. Once provisioned, you can connect Azure virtual networks and supported cloud-provider virtual networks through a private cloud-to-cloud connection. One to keep an eye on as it moves towards GA!

- [Standard service endpoint (Public Preview)](https://azure.microsoft.com/en-us/updates?id=561475) : Introducing a scalable and secure way to connect IaaS workloads to Azure PaaS services under the Private Link family. This [enhanced capability](https://learn.microsoft.com/en-gb/azure/private-link/service-endpoint-standard-overview) overcomes the scale and management limitations of traditional service endpoints by integrating with network security perimeter and using Public IPs as network identifiers, enabling large‑scale IaaS‑to‑PaaS connectivity with stronger security controls.