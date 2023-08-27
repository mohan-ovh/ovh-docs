---
title: Lista dos serviços e licenças incluídos (EN)
routes:
    canonical: '/pages/hosted_private_cloud/nutanix_on_ovhcloud/02-available-services'
excerpt: 'Presentation of the included services and licences in the Nutanix on OVHcloud offer'
updated: 2022-09-20
---

## Objective

This page lists the included Nutanix licences and services in the **Nutanix on OVHcloud** offer.

## Scope of included Nutanix licences and services in the Nutanix on OVHcloud offer

Only the Nutanix licences and services listed on this page are available in the Nutanix on OVHcloud offer.<br>
If the licence or service you are looking for is not available, please refer to the [Hosted Private Cloud GitHub roadmap](https://github.com/ovh/hosted-private-cloud-roadmap/projects/3) as a first step.

Nutanix on OVHcloud offers two licence packs:

- **Nutanix Standard Pack**
- **Nutanix Advanced Pack** includes licences and services from the **Nutanix Standard Pack**, plus additional licences and services to support more advanced uses such as higher-performance replication, multiple sites, advanced data encryption capabilities, and Disaster Recovery Plan options. 

### Base of common licences and services to both **Nutanix Standard** and **Nutanix Advanced licence packs**

The licences and services common to both licence packs are:

- **Nutanix Cloud Infrastructure (NCI)**, formerly **Hybrid Cloud Infrastructure** 
    - **AHV Virtualisation**: virtualisation integrated in NUTANIX ([presentation of Nutanix AHV](https://www.nutanix.com/products/ahv)).
    - **Nutanix Kubernetes Engine**: management of Kubernetes containers under Nutanix, a product formerly named **Karbon** ([presentation of Nutanix Kubernetes Engine](https://www.nutanix.com/products/karbon)).

- **Nutanix Cloud Manager(NCM)**, formerly **Cloud Management** ([presentation of Nutanix Cloud Management](https://www.nutanix.com/products/cloud-manager/aiops)).
    - **Intelligent Operation**, formerly **Prism Pro**: monitoring and forecasting of requirements.
    - **Flow**: network virtualisation and micro-segmentation ([FLOW presentation](https://www.nutanix.com/products/flow)).

- **Nutanix Unified Storage**, formerly **Unified Storage**.
    - **Block Storage Volumes**: Block storage for iSCSI access, either inside a Nutanix cluster for a particular use, or outside to provide access to Nutanix storage for other virtualised computers or infrastructures.

- **Framework utilities**
    + **X-ray**: a set of tools for testing and benchmarking the main hyperconverged solutions ([X-Ray presentation](https://www.nutanix.com/products/x-ray)).
    + **Move**:  migration tool to Nutanix ([MOVE presentation](https://www.nutanix.com/products/move)).
    + **LCM**: cluster update tool ([LCM presentation](https://www.nutanix.com/products/life-cycle-manager))

### Additional licences and services available with the **Nutanix Standard licence pack**

**Nutanix Standard** includes the **AOS Pro** version of **AOS Storage**, formerly known as **AOS Distributed Storage**, which allows:

- Distributed storage management
- Advanced orchestration
- Asynchronous replication with an *RPO* (Recovery Point Objective) of one hour.

### Additional licences and services available with the **Nutanix Advanced licence pack**

**Nutanix Advanced** includes the **AOS Ultimate** version of **AOS Storage**, formerly known as **AOS Distributed Storage**, which adds the following capabilities in addition to the standard version:

- Advanced replication with better cluster resilience:
    - **Nearsync Replication** with an **RPO** of 20 seconds.
    - **Metro Availability** with an **RPO** of 0 seconds and continuous use.
    - **Sync Replication** with an **RPO** at 0 seconds.
- and better security:
    - **Data-at-Rest Encryption**: software encryption.
    - **Native KVM**: encryption keys management.

For more information about the different versions of **AOS**, see the [Nutanix AOS options page](https://www.nutanix.com/products/software-options).

### Summary

Below is a summary table of the two OVHcloud Nutanix solutions:

| Solution name                 | Service Category                       | Service Feature                   |
| ----------------------------- | -------------------------------------- | --------------------------------- |
| **Nutanix Standard**          | **AOS Storage**                        | **AOS Pro**                       |
|                               | **Nutanix Cloud Infrastructure (NCI)** | **AHV Virtualization**            |
|                               |                                        | **Nutanix Kubernetes Engine**     |
|                               | **Nutanix Cloud Manager(NCM)**         | **Intelligent Operations**        |
|                               |                                        | **Flow**                          |
|                               | **Nutanix Unified Storage**            | **Volumes Block Storage**         |
|                               | **Framework Utilities**                | **X-ray**                         |
|                               |                                        | **Move**                          |
|                               |                                        | **Lcm**                           |
| **Nutanix Advanced**          | **AOS Storage**                        | **AOS Ultimate**                  |
|                               | **Nutanix Cloud Infrastructure (NCI)** | **AHV Virtualization**            |
|                               |                                        | **Nutanix Kubernetes Engine**     |
|                               | **Nutanix Cloud Manager(NCM)**         | **Intelligent Operations**        |
|                               |                                        | **Flow**                          |
|                               | **Nutanix Unified Storage**            | **Volumes Block Storage**         |
|                               | **Framework Utilities**                | **X-ray**                         |
|                               |                                        | **Move**                          |
|                               |                                        | **Lcm**                           |

## Go further

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](https://www.ovhcloud.com/pt/professional-services/) to get a quote and ask our Professional Services experts for assisting you on your specific use case of your project.

Join our community of users on <https://community.ovh.com/en/>.
