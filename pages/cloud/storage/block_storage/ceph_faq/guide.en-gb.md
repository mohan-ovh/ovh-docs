---
title: FAQ
slug: ceph/faq
excerpt: 'Frequently asked questions'
section: Cloud Disk Array
updated: 2020-11-05
---

**Last update 5th November 2020**


## What is Cloud Disk Array?
Cloud Disk Array (CDA) is a private, dedicated (on disk level) storage system powered by Ceph. During development and testing it was known as Ceph-as-a-Service. CDA gives you storage space that can be utilized in a number of ways:

- RADOS (low-level Ceph-specific object storage) - when building a custom application that depends on Ceph
- RBD (block devices) - can be used in dedicated servers with Linux or for VM disks in OpenStack and Proxmox environments
- CephFS (NFS-like filesystem) - provides distributed filesystem for all modern Linux distributions

There are also other ways to access Ceph which are not currently available for CDA:

- iSCSI gateway for RBD - for integration with existing environment with iSCSI support
- RGW (REST object storage) - can be used to build a CDN (with an OVH provided load-balancer)
- NFS and CIFS (SAMBA) gateways for CephFS - for integration with existing Windows or Linux environments
- inter-DC replication

Our goal is to provide to customers all features of Ceph inside a service managed by OVH. Let us know which interfaces you're interested in.


## Where is my data stored?
Once you select a Data Center, your data will be replicated three times. Those replicas are placed on three different server machines on three different racks.

To reduce latency when accessing your cluster, your clients should be in the same OVH datacenter as your Ceph cluster.


## Can I increase my Cloud Disk Array storage capacity?
Yes, you can increase size of you CDA through an API.


## Can I decrease my Cloud Disk Array storage capacity?
No - at the moment it is not possible.


## Can I deploy a filesystem over my Cloud Disk Array?
You can enable CephFS using API to have fully managed distributed filestystem.


## Is it possible to access a Cloud Disk Array from a service not hosted by OVH?
Short answer is: No - at the moment it is not possible.

In order to maximize performance and minimize latency for block devices (RBD) and fileystem (CephFS) it is only possible to use it inside OVH network - from other OVH services. If you need external access please contact us.

Please keep in mind that there are plans to add another mechanism for accessing CDA data storage - Rados Gateway. Rados Gateway will be able to expose CDA access to services located outside OVH via SWIFT API.


## Which OVH solutions are compatible with Cloud Disk Array?
Any solutions that can connect to the OVH local network.

Public Cloud, Dedicated Server, Private Cloud Computing (PCC), VPS.


## How is ensured the High Availability of the Cloud Disk Array solution?
Cloud Disk Array is powered by Ceph, which is a storage solution with no single point of failure.

Whichever protocol you use to store your data in Ceph, it is stored internally as RADOS objects. Each object is replicated 3 times across 3 different servers in 3 different racks.

In case of 1 replica failure, there is no disruption for client (except for slight performance degradation because of recovery).

In case of 2 replica failures, client access is blocked to the degraded objects until they are replicated at least 2 times. This is done in order to prevent data loss.

## Go further

Visit our dedicated Discord channel: <https://discord.gg/ovhcloud>. Ask questions, provide feedback and interact directly with the team that builds our Storage and Backup services.

Join our community of users on <https://community.ovh.com/en/>.
