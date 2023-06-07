---
title: PostgreSQL - Capabilities and Limitations
excerpt: Discover the capabilities and limitations of Public Cloud Databases for PostgreSQL
routes:
    canonical: '/pages/platform/databases/postgresql_01_capabilities'
updated: 2023-05-03
---

**Last updated May 3rd, 2023**

## Objective

This page provides the technical capabilities and limitations of the Public Cloud Databases for PostgreSQL offer.

We continuously improve our offers. You can follow and submit ideas to add to our roadmap at <https://github.com/ovh/public-cloud-roadmap/projects/2>.

## Capabilities and limitations

### Supported regions and multi-AZ

The Public Cloud Databases offer is available in the following regions:

- `BHS` (Beauharnois, Canada)
- `DE` (Frankfurt, Germany)
- `GRA` (Gravelines, France)
- `SBG` (Strasbourg, France)
- `UK` (London, United Kingdom)
- `WAW` (Warsaw, Poland)

Database nodes have to be in the same region. Multi-AZ is currently not supported.

### PostgreSQL versions

The Public Cloud Databases offer supports the following PostgreSQL versions:

- PostgreSQL 11
- PostgreSQL 12
- PostgreSQL 13
- PostgreSQL 14
- PostgreSQL 15

Please refer to the [DBMS lifecycle policy guide](/pages/platform/databases/information_02_lifecycle_policy) for recommendations on version upgrades and end of life announcements of major versions. Additionally, you can follow the EOL lifecycle for PostgreSQL version on their official page : <https://www.postgresql.org/support/versioning/>

### PostgreSQL connectors

You can use any of the [PostgreSQL-recommended drivers and extensions](https://www.postgresql.org/download/product-categories/){.external} to access your instance.

### Plans

Three plans are available:

- *Essential*
- *Business*
- *Enterprise*

Here is an overview of the various plans' capabilities:

| Plan         | Number of nodes by default | Read replicas |
| ------------ | -------------------------- | ------------- |
| *Essential*  | 1                          | No            |
| *Business*   | 2                          | Planned       |
| *Enterprise* | 3                          | Planned       |

Your choice of plan affects the number of nodes your cluster can run, the SLA, and a few other features such as read replicas or backup retention.

> [!primary]
> Be aware that you will be able to upgrade your plan but you won't be able to downgrade it afterwards.

#### Nodes and replicas

- **Essential**: the cluster can support at most one node.
- **Business**: the cluster is delivered with 2 nodes by default. Adding read replicas is planned.
- **Enterprise**: the cluster is delivered with 3 nodes by default. Adding read replicas is planned.

#### License type

PostgreSQL software is under the PostgreSQL License, a liberal open-source license, similar to BSD or MIT licenses.
More information on <https://www.postgresql.org/about/licence/>.

### Hardware resources

Here are the node types you can choose from:

| Name    | Storage                 | vCore | Memory (GB) |
| ------- | ----------------------- | ----- | ----------- |
| db1-4   | From 80 GB to 240 GB    | 2     | 4           |
| db1-7   | From 160 GB to 480 GB   | 2     | 7           |
| db1-15  | From 320 GB to 960 GB   | 4     | 15          |
| db1-30  | From 640 GB to 1.92 TB  | 8     | 30          |
| db1-60  | From 1.28 TB to 3.84 TB | 16    | 60          |
| db1-120 | From 2.56 TB to 7.68 TB | 32    | 120         |

Right now, all nodes of a given cluster should be of the same type and distributed in the same region.

#### Flexible storage

You can increase the storage of your cluster up to the maximum allowed for a given reference. Please refer to the [Resize your cluster storage guide](/pages/platform/databases/databases_11_resize_your_cluster_storage) for more information.

#### Node template upgrade

You can upgrade the node template of your cluster to scale your hardware resources up. This operation causes no interruption of service but be aware that you will not be able to downgrade the node template afterwards.

#### Disk type

The type of storage available may vary according to the region your cluster lives in: see [Availability of Public Cloud products](https://www.ovhcloud.com/it/public-cloud/regions-availability/) for more information about block storage type availability depending on region. Thus, your cluster may be backed by e.g. *High Speed* or *High Speed Gen2* block storage.

Also, the performance characteristics of the various storage offerings may vary depending on e.g. the storage size your cluster uses: *High Speed* may offer better iops than *High Speed Gen2* for some disk sizes. See [Block Storage documentation](https://www.ovhcloud.com/it/public-cloud/block-storage/) for more information about those performance characteristics.

Public Cloud Databases will select the most efficient disk type for your cluster depending on your cluster parameters.

#### Effective storage

The disk size listed above is the total disk size of the underlying machine. However, a small part of it goes towards the OS install.

We try hard to avoid "disk full" situations that could be harmful to cluster health. Therefore:

1. When reaching a concerning level of disk usage, a warning email is sent.
2. When reaching a concerning level of disk usage, the service is moved in the "DISK_FULL" state, and "read-only" mode, meaning no more writes can be done.
3. You then have the ability to upgrade to a higher service plan with more storage.

See the [Handling «Disk Full» situations documentation](/pages/platform/databases/databases_10_full_disk_handling) for more information.

### Features

#### Network
PostgreSQL clusters are reachable through default port 5432.

Public as well as private networking (vRack) can be used for all the offers.

Ingress and Egress traffic are included in the service plans and unmetered.

##### Private network considerations
Here are some considerations to take into account when using private network:

- Network ports are created in the private network of your choice. Thus, further operations on that network might be restricted - e.g. you won’t be able to delete the network if you didn’t stop the Public Cloud Databases services first.
- When connecting from an outside subnet, the Openstack IP gateway must be enabled in the subnet used for the Database service. The customer is responsible for any other custom network setup.

##### Authorised IPs

Once your service is up and running, you will be able to specify IP addresses (or CIDR blocks) to authorise incoming traffic. Until then, your service will be unreachable. 

#### Maximum simultaneous connections

The number of simultaneous connections in Public Cloud Databases for PostgreSQL depends on the available total memory on the node.
We allow approximately 100 connections per 4 GB of RAM memory, capped to a maximum of 1000 active connections.

So for example on a server with 7 GB memory, you will get approximately 200 connections and with 15 GB memory you will get 400 connections.

#### Advanced parameters

You can further customise your PostgreSQL by using advanced parameters. See the [Advanced parameters references documentation](/pages/platform/databases/postgresql_10_advanced_parameters_references) for more information on the supported parameters.

#### Backups

*Essential* plan clusters are automatically backed up daily during their maintenance window. Backup retention is 2 days.

*Business* plan clusters are automatically backed up daily during their maintenance window. Backup retention is 14 days.

*Enterprise* plan clusters are automatically backed up daily during their maintenance window. Backup retention is 30 days.

#### Logs and metrics

Logs and metrics are available through the Control Panel and the API. Additionally, cross service integration can be configured to leverage your logs and metrics in other Public Cloud Database services. You could then view your PostgreSQL logs in Opensearch and metrics in Grafana. See the [Cross Service Integration documentation](/pages/platform/databases/databases_07_cross_service_integration) for more information.

- **Logs retention**: 1000 lines of logs
- **Metrics retention**: 1 calendar month

Please note that if the database instance is deleted, logs and metrics are also automatically deleted.

#### Users and roles

Creation of users is allowed via the Control Panel and API with default admin roles and privileges.
You can't select specific privileges.

## We want your feedback!

We would love to help answer questions and appreciate any feedback you may have.

Are you on Discord? Connect to our channel at <https://discord.gg/ovhcloud> and interact directly with the team that builds our databases service!
