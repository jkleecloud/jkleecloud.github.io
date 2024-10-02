+++
title = 'Application Gateway Migration - V1 SKU-V2 SKU - Notes'
date = 2024-10-02T11:03:40+01:00
draft = false
categories = ['Tech Posts']
tags = ['Application Gateway']
+++

This post captures some of the key details I've noted while looking at migrating Application Gateways from the V1 SKU to V2:

- Migration Path
- Key config differences between V1 and V2, and between the standard and Private deployment models for V2
- Subnets
- Sizing, Pricing and Resilience
- Outline upgrade steps

# Background

Application Gateways (AGs) are used to support load balancing, traffic management and certificate management for applications. Since the initial launch of the V1 SKU, an AG V2 SKU has been introduced with improved performance and additional features. Microsoft have announced that the Application Gateway V1 SKU will be retired on 28th April 2026; no new V1 deployments have been allowed since 28th August 2024. If you haven’t already, you should begin planning to upgrade your Application Gateways to the V2 SKU.

# Migration Path V1-V2

There is no direct migration path to upgrade existing V1 AG instances to the V2 SKU. A new AG must be deployed using the V2 SKU (into a new subnet) and the configuration from the V1 AG migrated to it; traffic must then be redirected to the new V2 AG.

[Microsoft provide a script](https://learn.microsoft.com/en-us/azure/application-gateway/migrate-v1-v2#using-the-script) that can perform the following tasks:

- Create a new subnet (it is optional to create a new one - an existing one can also be specified, but this must have been created in advance)
- Create a new V2 Application Gateway instance
- Copy configuration from V1 AG to V2 AG

# Key configuration differences between V1 and V2

## Backend certificates

The V1 AG uses authentication certificates for each backend server instance (e.g. *servername*.cer). V2 AGs require the trusted root certificate for the backend server certificates to be uploaded instead (again in .cer format (public key)). Only 1 certificate is thus required, rather than 1 for each backend.

## TLS/SSL certificates (front-end)

V1 AGs require TLS certificates to be attached to the listener to perform TLS termination. This model can still be used with V2 AGs and is the configuration applied by the Microsoft migration script - the TLS certificates required must be provided as input objects to the script (so they will either need to be retrieved separately or downloaded from the V1 AGs prior to migration).
V2 AGs can also reference certificates stored in a Key Vault. ([Per Microsoft documentation](https://learn.microsoft.com/en-us/azure/application-gateway/key-vault-certs#verify-firewall-permissions-to-key-vault), while Key Vaults behind Private Endpoints can be used with V2 AGs, the private DNS zone containing the corresponding DNS record must be linked to the VNet containing the AG, even if custom DNS servers are being used. This may cause an issue with using Key Vaults if you’re using custom DNS and managing zones for Private Link yourself, rather than using Azure DNS.)

## Public IP address

If used internally rather than being Internet-facing, the current deployment model for V1 AGs is fully private - they do not have any public IP addresses. At present, V2 AGs require a public IP address for Azure management traffic even if used internally. The fully [private deployment of V2 App Gateways has been in public preview since July 2023](https://learn.microsoft.com/en-us/azure/application-gateway/application-gateway-private-deployment) and as of the time of writing remains in preview - this configuration aligns more closely with the V1 deployment model and removes the requirement for a public IP address.

[Microsoft state that when Private V2 AGs go GA](https://learn.microsoft.com/en-us/azure/application-gateway/migrate-v1-v2#caveatslimitations) it will be possible to use their script to transfer a V1 configuration to a private V2 AG configuration. A public IP address will need to be created for each new V2 AG at present - the MS migration script will automatically create one if it is not specified. Note that at present there also does not seem to be a migration path from the current V2 deployment model to a private deployment - [the AG must be redeployed](https://learn.microsoft.com/en-us/azure/application-gateway/application-gateway-private-deployment?tabs=portal#coexisting-v2-application-gateways-created-prior-to-enablement-of-enhanced-network-control).

## NSG Rules

[NSG rule requirements for the V2 SKU](https://learn.microsoft.com/en-us/azure/application-gateway/configuration-infrastructure#network-security-groups) are broadly the same as for V1, with a few minor differences/updates:

- The required inbound rule for AG backend health communication uses different destination ports for V2 (65200-65535). There is also now a GatewayManager service tag which can be used as the Source instead of Internet.
- Outbound traffic must be allowed to the Internet for all destinations (Any source, Any ports, Any destination) at least until Private V2 deployments are available, for which [a 'deny all outbound' rule](https://learn.microsoft.com/en-us/azure/application-gateway/application-gateway-private-deployment?tabs=portal#outbound-rules) seems to be [explicitly supported](https://learn.microsoft.com/en-us/azure/application-gateway/application-gateway-private-deployment?tabs=portal#introduction).
- The rule allowing traffic inbound from the AzureLoadBalancer service tag is still required.

Once Private V2 AG deployments become available, [the GatewayManager inbound and Internet outbound rules will no longer be required](https://learn.microsoft.com/en-us/azure/application-gateway/application-gateway-private-deployment?tabs=portal#network-security-group-control) - only the inbound Azure Load Balancer rule will still be needed.

## Route Tables/Routes

The use of the 0.0.0.0/0 'catch-all' route for forced tunnelling [is not supported with V2 AGs](https://learn.microsoft.com/en-us/azure/application-gateway/configuration-infrastructure#supported-user-defined-routes). (This route also had to be removed (if used) to enable V1 AG metrics to work, but it is explicitly unsupported with V2 AGs at present). Once Private V2 AG deployments become available, [this restriction will not apply](https://learn.microsoft.com/en-us/azure/application-gateway/application-gateway-private-deployment?tabs=portal#route-table-control) and it will be possible to include the forced tunnelling route in the V2 AG subnet route tables if needed.

# Subnets
In common with V1 AGs, V2 AGs cannot share a subnet with any other Azure resources; they also cannot share a subnet with V1 AGs. An entirely new subnet must be created with sufficient space for the AG itself and any scaling. AGs use 1 IP address per instance + 1 for a private FE IP. A CIDR /24 subnet (256 IP addresses, with 251 available when platform reservations are accounted for) is not required but it is [MS's recommendation](https://learn.microsoft.com/en-us/azure/application-gateway/configuration-infrastructure#size-of-the-subnet). Traffic analysis of existing AGs should indicate how many instances are required as a baseline - a view can then be taken as to how much more space may be needed for scaling to define the size of the subnet.

# Sizing, Pricing and Resilience
V1 AGs come in Small, Medium and Large sizes within the SKU. Pricing is based on a fixed cost per provisioned hour for the AG based on size (Small cheapest, Large most expensive) and number of instances deployed; plus a data processing charge depending on AG size and amount of data processed by the gateway.

V2 AGs do not have sizes within the SKU. A fixed charge is applied for each hour the gateway (in its entirety) is provisioned. An additional variable charge is applied based on the amount of processing capacity required to handle the traffic - this is referred to as a [Capacity Unit (CU)](https://learn.microsoft.com/en-us/azure/application-gateway/understanding-pricing#capacity-unit).

Within each V2 AG deployment, a number of instances are specified (a minimum of 2 is recommended for high availability if scaling manually). Each instance provides a number of capacity units - [a minimum of 10 is guaranteed per instance](https://learn.microsoft.com/en-us/azure/application-gateway/understanding-pricing#instance-count). Each CU provides a number of persistent connections; an amount of data throughput (Mbps); and 1 compute unit (dealing with TLS connections, URL rewrites, etc. - can handle approx. 50 connections per second with an RSA 2048-bit TLS certificate [per MS documentation](https://learn.microsoft.com/en-us/azure/application-gateway/understanding-pricing#compute-unit)). Thus correct sizing of a V2 AG depends on provisioning the correct number of instances to handle the expected traffic.

The fixed cost does not change with the number of instances deployed - only the CU cost increases. (The fixed cost also includes the cost for the public IP address – it’ll be interesting to see if the Private deployment is slightly cheaper at GA given it doesn't need the public IP!)

V2 AGs can also be configured to Autoscale (not available with V1 AGs) - a minimum instance count is specified (reserved CUs, which are billed regardless of consumption) and additional capacity units can be provisioned if the traffic load exceeds the reserved capacity (additional variable charge). [V2 AGs are always highly available](https://learn.microsoft.com/en-us/azure/application-gateway/application-gateway-autoscaling-zone-redundant#autoscaling-and-high-availability) even if autoscaling is set to zero instances; however, it takes time to provision a new instance ([6-7 minutes per MS documentation](https://learn.microsoft.com/en-us/azure/application-gateway/application-gateway-autoscaling-zone-redundant#autoscaling-and-high-availability)).

# Outline Steps to upgrade 

For each AG to be migrated:

- Retrieve TLS certificates (frontend/listener) – can be downloaded from V1 AGs with [PowerShell](https://learn.microsoft.com/en-us/powershell/module/az.network/get-azapplicationgatewaysslcertificate?view=azps-10.0.0)
- Retrieve root certificate (backend - .cer)
- Create subnet for V2 AG(s) 
- Configure NSG for V2 AG subnet
- Create public IP address
- Run migration script
- Test new AG
- Repoint application DNS entries to new private FE IP on V2 AG
