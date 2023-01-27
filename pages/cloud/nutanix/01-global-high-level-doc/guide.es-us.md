---
title: Documentación general de Nutanix (EN)
slug: high-level-documentation
routes:
    canonical: 'https://docs.ovh.com/gb/en/nutanix/high-level-documentation/'
excerpt: Technical details of the Nutanix infrastructure at OVHcloud
section: Primeros pasos
order: 01
updated: 2022-12-08
---

**Last updated 8th December 2022**

## Objective

This page provides an explanation of the elements that constitute a Nutanix cluster as delivered by OVHcloud and how it functions on the OVHcloud infrastructure.

### Main characteristics

A Nutanix cluster consists of a stack of OVHcloud services:

- [Dedicated server](https://www.ovhcloud.com/es/bare-metal/)
- [vRack](https://www.ovh.com/world/es/soluciones/vrack/)
- [Load Balancer](https://www.ovh.com/world/es/soluciones/load-balancer/)
- [Additional IP](https://www.ovhcloud.com/es/bare-metal/ip/)

Dedicated servers (3 minimum) are connected within the vRack which is an L2 network, the hosts (node) private network.

Two VLANs are used, VLAN 0 for public internet and VLAN 1 for Nutanix infrastructure (Hosts, CVMs, Prism Element and Prism Central).

The public IP address of each node is not accessible since the Additional IP is dedicated to the Internet access. This access is ensured by the "OVHGateway" wich is a dedicated VM created by OVHcloud on your cluster.

The load balancer is used to expose the **Prism Central** WebUI to the public Internet. For security reasons, you are able to restrict the WebUI to IP addresses of your organisation.

![diagram image](images/infra1.png){.thumbnail}

### Sizing

Your cluster requires some features to work properly. After delivery your cluster will have 5 VMs (for a 3 node cluster).
Each node will have a "CVM". In the cluster you will find two more VMs: Prism Central and the OVHgateway. 

### Prism Central

Prism Central is deployed in the "small" configuration.

It can furthermore work in two modes: "Alone" (1 VM) or "Scale" (3 VM). It can manage up to 2500 VMs in general.

- `Alone mode`: 6 vCPUs, 26 GB of memory, and 500 GiB of storage.
- `Scale mode` (for better resiliency and more capacity): 18 vCPUs, 78 GB of memory, and 1500 GiB of storage (combined).

In case of doubt, choose the "Alone" mode. You can always switch to "Scale" mode later.

### CVMs

All CVMs require 32 GB of minimum memory and 12 vCPUs for each node.
You will need to increase these values if you add new features on your cluster.

### OVHgateway

**The OVHgateway provides Internet access to the cluster via the Additional IP address.**

This VM uses two network cards (in the vRack), one for the private network on VLAN 1, the other one for the public internet on VLAN 0.

The VM uses NAT to route traffic from the private network to the Internet.
You can therefore use it for outgoing traffic but not for incoming traffic.

OVHgateway has a lightweight design, using 1 vCPU, 1 GB memory and a 11 GiB disk.

Bandwidth for Internet access is 1 Gbps.

To replace this virtual machine with another network operating system, please read this guide: [Replace OVHgateway](https://docs.ovh.com/us/es/nutanix/software-gateway-replacement/).

### Prism Central Access

Once the cluster is delivered, OVHcloud provides you with a FQDN for your cluster.

Acces to Prism Central is available under `https://<fqdn>:9440`. This access is provided through the load balancer. 

## Go further

Join our community of users on <https://community.ovh.com/en/>.