---
title: Cassandra - Capabilities and Limitations
excerpt: Discover the capabilities and limitations of Public Cloud Databases for Cassandra
routes:
    canonical: '/pages/public_cloud/public_cloud_databases/cassandra_01_capabilities'
updated: 2023-08-17
---

## Objective

This page provides the technical capabilities and limitations of the Public Cloud Databases' Cassandra offer.

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

Entire database instances have to be in the same region. Multi-AZ is currently not supported.

### Cassandra versions

The Public Cloud Databases offer supports the following Cassandra versions:

- Cassandra 4.0

Cassandra recommends always installing and using the latest stable version.

### Plans

Three plans are available:

- *Essential*
- *Business*
- *Enterprise*

Here is an overview of the various plans' capabilities:

| Plan         | Number of nodes by default | Read replicas  |
| ------------ | -------------------------- | -------------  |
| *Essential*  | 3                          | No             |
| *Business*   | 3                          | Planned        |
| *Enterprise* | 6                          | Planned        |

Your choice of plan affects the number of nodes your cluster can run, the SLA, and a few other features such as read replicas or backup retention.

#### Nodes and replicas

- **Essential**: The cluster is delivered with 3 nodes by default.
- **Business**: The cluster is delivered with 3 nodes by default. Adding read replicas is planned.
- **Enterprise**: The cluster is delivered with 6 nodes by default. Adding read replicas is planned.

#### License type

Each cluster is provided with the Cassandra Community (GPL) license.

If any, license cost is included inside the service plans. You can't bring your own licenses.

### Hardware resources

Here are the node types you can choose from:

**Essentials plans**

| Name    | Storage                | vCore | Memory (GB) |
| ------- | ---------------------- | ----- | ----------- |
| db1-4   | From 240 GB to 720 GB  | 1     | 4           |
| db1-7   | From 480 GB to 1.44 TB | 2     | 7           |

**Business plans**

| Name    | Storage                  | vCore | Memory (GB) |
| ------- | ------------------------ | ----- | ----------- |
| db1-15  | From 960 GB to 2.88 TB   | 4     | 15          |
| db1-30  | From 1.92 TB to 5.76 TB  | 8     | 30          |
| db1-60  | From 3.84 TB to 11.52 TB | 16    | 60          |
| db1-120 | From 7.68 TB to 23.04 TB | 32    | 120         |

**Enterprise plans**

| Name    | Storage                   | vCore | Memory (GB) |
| ------- | ------------------------- | ----- | ----------- |
| db1-15  | From 1.92 TB to 5.76 TB   | 4     | 15          |
| db1-30  | From 3.84 TB to 11.52 TB  | 8     | 30          |
| db1-60  | From 7.68 TB to 23.04 TB  | 16    | 60          |
| db1-120 | From 15.36 TB to 46.08 TB | 32    | 120         |

Right now, all nodes of a given cluster should be of the same type and live in the same region.

#### Flexible storage

You can increase the storage of your cluster up to the maximum allowed for a given reference. Please refer to the [Resize your cluster storage guide](/pages/public_cloud/public_cloud_databases/databases_11_resize_your_cluster_storage) for more information.

#### Node template upgrade

You can upgrade the node template of your cluster to scale your hardware resources up. This operation causes no interruption of service but be aware that you will not be able to downgrade the node template afterwards.

#### Disk type

The type of storage available may vary according to the region your cluster lives in: see [Availability of Public Cloud products](https://www.ovhcloud.com/it/public-cloud/regions-availability/) for more information about block storage type availability depending on region. Thus, your cluster may be backed by e.g. *High Speed* or *High Speed Gen2* block storage.

Also, the performance caracteristics of the various storage offerings may vary depending on e.g. the storage size your cluster uses: *High Speed* may offer better iops than *High Speed Gen2* for some disk sizes. See [Block Storage documentation](https://www.ovhcloud.com/it/public-cloud/block-storage/) for more information about those performance caracteristics.

Public Cloud Databases will select the most efficient disk type for your cluster depending on your cluster parameters.

#### Effective storage

The disk size listed above is the total disk size of the underlying machine. However, a small part of it goes towards the OS install.

We try hard to avoid "disk full" situations that could be harmful to cluster health. Therefore:

1. When reaching a concerning level of disk usage, a warning email is sent.
2. When reaching a concerning level of disk usage, the service is moved in the "DISK_FULL" state, and "read-only" mode, meaning no more writes can be done.

See the [Handling «Disk Full» situations documentation](/pages/public_cloud/public_cloud_databases/databases_10_full_disk_handling) for more information.

### Features

#### Network
Public as well as private networking (vRack) can be used for all the offers.

Ingress and Egress traffic are included in the service plans and unmetered.

##### Private network considerations
Here are some considerations to take into account when using private network:

- Network ports are created in the private network of your choice. Thus, further operations on that network might be restricted - e.g. you won’t be able to delete the network if you didn’t stop the Public Cloud Databases services first.
- When connecting from an outside subnet, the Openstack IP gateway must be enabled in the subnet used for the Database service. The customer is responsible for any other custom network setup.
- Subnet sizing should include considerations for service nodes, other co-located services within the same subnet, and an allocation of additional available IP addresses for maintenance purposes. Failure to adequately size subnets could result in operational challenges and the malfunctioning of services.

##### Authorised IPs

Once your service is up and running, you will be able to specify IP addresses (or CIDR blocks) to authorise incoming traffic. Until then, your service will be unreachable.

#### Advanced parameters

You can further customise your Cassandra by using advanced parameters. See the [Advanced parameters references documentation](/pages/public_cloud/public_cloud_databases/cassandra_03_advanced_parameters_references) for more information on the supported parameters.

#### Backups

Your services are automatically backed up daily during their maintenance window. The point-in-time recovery (PITR) feature is currently not available.

See the [Automated Backups guide](/pages/public_cloud/public_cloud_databases/databases_05_automated_backups) for more information.

#### Logs and metrics

Logs and metrics are available through the Control Panel and the API. Additionally, cross service integration can be configured to leverage your logs and metrics in other Public Cloud Database services. You could then view your Cassandra logs in Opensearch and metrics in Grafana (metrics have to be exported first in a time series compatible engine such as PostgreSQL or M3db). See the [Cross Service Integration documentation](/pages/public_cloud/public_cloud_databases/databases_07_cross_service_integration) for more information.

- **Logs retention**: 1000 lines of logs
- **Metrics retention**: 1 calendar month

Please note that if the database instance is deleted, logs and metrics are also automatically deleted.

## We want your feedback!

We would love to help answer questions and appreciate any feedback you may have.

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](https://www.ovhcloud.com/it/professional-services/) to get a quote and ask our Professional Services experts for a custom analysis of your project.

Are you on Discord? Connect to our channel at <https://discord.gg/ovhcloud> and interact directly with the team that builds our databases service!
