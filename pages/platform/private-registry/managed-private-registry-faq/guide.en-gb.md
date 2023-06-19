---
title: 'FAQ Managed Private Registry (Harbor)'
updated: 2023-05-09
---

**Last updated 9th May, 2023.**

## Objective
Here are the most frequently asked questions about Managed Private Registry (Harbor).

### In which regions is the Private Registry solution available?
Private Registry is currently available in Western Europe (**GRA**/**DE** regions) and North America (**BHS** region).

### What are the Managed Private Registry service dependencies?

The MPR (Managed Private Registry) service is managed by our teams relying on compute resources and network from Public Cloud and on Object Storage S3 standard. Those dependencies are neither visible, nor billed.

Find below the exact locations of the dependencies:

| X              | Dependencies | Public Cloud<br>(Compute/Network) | Object Storage S3 standard |
|----------------|:------------:|:---------------------------------:|:--------------------------:|
| **MPR region** |      X       |                 X                 |             X              |
| GRA            |      X       |               GRA7                |            GRA             |
| BHS            |      X       |               BHS5                |            BHS             |
| DE             |      X       |                DE1                |             DE             |

### What version of Harbor is offered?
All new Private Registry services expose Harbor 2.x. We regularly backport security and performance patches from the latest versions and will regularly propose new feature upgrades.

#### Tips and Tricks
All traffic to and from the registry is completely **free**.

### What service levels are included in the Private Registry service?
Private Registry is covered by a service level (SLA) that guarantees very high availability to give you the assurance of a high efficiency of your developments and deployments. **M** and **L** plans have an SLA that also covers components such as the user interface and vulnerability scanning. You will find all the details in the [Special Conditions for OVHcloud Public Cloud Service](https://www.ovhcloud.com/en-gb/terms-and-conditions/contracts/){.external}.

### Do I have to use the OVHcloud Managed Kubernetes Service with Private Registry?
No, because by subscribing to the Private Registry service you will have your own Docker Registry and your own [Harbor](https://goharbor.io/) (API and GUI). Once you receive your IDs, you will be able to use the Private Registry service with any container or orchestrator tool, the OVHcloud Kubernetes solution or another one.

### As a Private Registry user, do I have the option to switch plans?
You can migrate to a plan with larger capacity at any time. As soon as you notify us of your wish for evolution, the new limits are taken into account in tens of seconds **without any data loss** or configuration changes required.

#### Tips and Tricks
If you create, edit or delete your service during the month, you will be billed only for the hours actually used. Depending on your choice of plan, you can have up to 5 TB of storage capacity. For each of the plans, unlimited traffic is included, regardless of its destination.

## Go further

Join our community of users on <https://community.ovh.com/en/>.
