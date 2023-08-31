---
title: OpenSearch - Capabilities and Limitations
excerpt: Discover the capabilities and limitations of Public Cloud Databases for OpenSearch
updated: 2023-08-17
---

## Objective

This page provides the technical capabilities and limitations of the Public Cloud Databases for OpenSearch offer.

We continuously improve our offers. You can follow and submit ideas to add to our roadmap at <https://github.com/ovh/public-cloud-roadmap/projects/2>.

## Capabilities and limitations

### Supported regions and multi-AZ

The Public Cloud Databases offer is available in the following regions:

- `BHS` (Beauharnois, Canada)
- `DE` (Frankfurt, Germany)
- `GRA` (Gravelines, France)
- `SBG`(Strasbourg, France)
- `UK` (London, United Kingdom)
- `WAW` (Warsaw, Poland)

Database nodes have to be in the same region. Multi-AZ is currently not supported.

### OpenSearch versions

The Public Cloud Databases offer supports the following OpenSearch versions:

- OpenSearch 1
- OpenSearch 2

Please refer to the [DBMS lifecycle policy guide](/pages/public_cloud/public_cloud_databases/information_02_lifecycle_policy) for recommendations on version upgrades and end of life announcements of major versions. Additionally, you can follow the OpenSearch version history on their official page: <https://opensearch.org/docs/latest/version-history/>

### OpenSearch clients and plugins compatibility

You can use any of the [OpenSearch-recommended clients and plugins](https://opensearch.org/docs/latest/clients/index/#){.external} to access and populate your instance.

### Plans

Three plans are available:

- *Essential*
- *Business*
- *Enterprise*

Here is an overview of the various plans' capabilities:

| Plan         | Number of nodes by default | Additional Read replicas |
| ------------ | -------------------------- | ------------------------ |
| *Essential*  | 1                          | No                       |
| *Business*   | 3                          | Planned                  |
| *Enterprise* | 6                          | Planned                  |

Your choice of plan affects the number of nodes your cluster can run, the SLA, and a few other features such as read replicas or backup retention.

> [!primary]
> Be aware that you will be able to upgrade your plan but you won't be able to downgrade it afterwards.

#### Nodes and replicas

- **Essential**: the cluster can support at most one node.
- **Business**: the cluster is delivered with 3 nodes by default.
- **Enterprise**: the cluster is delivered with 6 nodes by default.

#### License type

OpenSearch software is under the Apache 2.0 license, a liberal open-source license.
More information on <https://github.com/opensearch-project/>.

### Hardware resources

Here are the node types you can choose from:

**Essentials plans**

| Name    | Storage               | vCore | Memory (GB) |
| ------- | ----------------------| ----- | ----------- |
| db1-4   | From 40 GB to 120 GB  | 2     | 4           |
| db1-7   | From 80 GB to 240 GB  | 2     | 7           |
| db1-15  | From 160 GB to 480 GB | 4     | 15          |

**Business plans**

| Name    | Storage                  | vCore | Memory (GB) |
| ------- | ------------------------ | ----- | ----------- |
| db1-7   | From 240 GB to 720 GB    | 2     | 7           |
| db1-15  | From 480 GB to 1.44 TB   | 4     | 15          |
| db1-30  | From 960 GB to 2.88 TB   | 8     | 30          |
| db1-60  | From 1.92 TB to 5.76 TB  | 16    | 60          |
| db1-120 | From 3.84 TB to 11.52 TB | 32    | 120         |

**Enterprise plans**

| Name    | Storage                  | vCore | Memory (GB) |
| ------- | ------------------------ | ----- | ----------- |
| db1-7   | From 480 GB to 1.44 TB   | 2     | 7           |
| db1-15  | From 960 GB to 2.88 TB   | 4     | 15          |
| db1-30  | From 1.92 TB to 5.76 TB  | 8     | 30          |
| db1-60  | From 3.84 TB to 11.52 TB | 16    | 60          |
| db1-120 | From 7.68 TB to 23.04 TB | 32    | 120         |

Right now, all nodes of a given cluster should be of the same type and distributed in the same region.

#### Flexible storage

You can increase the storage of your cluster up to the maximum allowed for a given reference. Please refer to the [Resize your cluster storage guide](/pages/public_cloud/public_cloud_databases/databases_11_resize_your_cluster_storage) for more information.

#### Node template upgrade

You can upgrade the node template of your cluster to scale your hardware resources up. This operation causes no interruption of service but be aware that you will not be able to downgrade the node template afterwards.

#### Disk type

The type of storage available may vary according to the region your cluster lives in: see [Availability of Public Cloud products](https://www.ovhcloud.com/pt/public-cloud/regions-availability/) for more information about block storage type availability depending on region. Thus, your cluster may be backed by e.g. *High Speed* or *High Speed Gen2* block storage.

Also, the performance caracteristics of the various storage offerings may vary depending on e.g. the storage size your cluster uses: *High Speed* may offer better iops than *High Speed Gen2* for some disk sizes. See [Block Storage documentation](https://www.ovhcloud.com/pt/public-cloud/block-storage/) for more information about those performance caracteristics.

Public Cloud Databases will select the most efficient disk type for your cluster depending on your cluster parameters.

#### Effective storage

The disk size listed above is the total disk size of the underlying machine. However, a small part of it goes towards the OS install.

We try hard to avoid "disk full" situations that could be harmful to cluster health. Therefore:

1. When reaching a concerning level of disk usage, a warning email is sent.
2. When reaching a concerning level of disk usage, the service is moved in the "DISK_FULL" state, and "read-only" mode, meaning no more writes can be done.
3. You then have the ability to upgrade to a higher service plan with more storage.

See the [Handling «Disk Full» situations documentation](/pages/public_cloud/public_cloud_databases/databases_10_full_disk_handling) for more information.

### Features

#### Plugin enabled by default

Here is the list of plugins enabled by default:

    ICU Analysis
    Phonetic Analysis
    kuromoji (Japanese Analysis)
    Mapper Size
    Open Distro for Elasticsearch SQL plugin
    Open Distro for Elasticsearch Alerting plugin
    Anomaly detection
    Asynchronous search
    Index Management
    k-NN
    Notebooks
    Performance Analyzer
    OpenSearch Dashboards Reports
    Scheduler for Dashboards Reports
    OpenSearch Dashboards GANTT Charts
    OpenSearch Dashboards Trace Analytics

#### Network
OpenSearch clusters are reachable through port specified in the control panel or API, for example 23125.

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

You can further customise your OpenSearch by using advanced parameters. See the [Advanced parameters references documentation](/pages/public_cloud/public_cloud_databases/opensearch_03_advanced_parameters_references) for more information on the supported parameters.

#### Backups

*Essential* plan clusters are automatically backed up hourly and daily during their maintenance window. Backup retention is 24 hours for hourly backups and 2 days for daily backups.

*Business* plan clusters are automatically backed up hourly and daily during their maintenance window. Backup retention is 24 hours for hourly backups and 14 days for daily backups.

*Enterprise* plan clusters are automatically backed up hourly and daily during their maintenance window. Backup retention is 24 hours for hourly backups and 30 days for daily backups.

See the [Automated Backups guide](/pages/public_cloud/public_cloud_databases/databases_05_automated_backups) for more information.

#### Logs and metrics

Logs and metrics are available through the Control Panel and the API. Additionally, cross service integration can be configured to leverage your logs and metrics in other Public Cloud Database services. You could then view your OpenSearch metrics in Grafana. See the [Cross Service Integration documentation](/pages/public_cloud/public_cloud_databases/databases_07_cross_service_integration) for more information.

- **Logs retention**: 1000 lines of logs
- **Metrics retention**: 1 calendar month

Please note that if the database instance is deleted, logs and metrics are also automatically deleted.

#### Access control (ACL)

We support index-level access control lists (ACL) to control permissions. This approach allows you to limit the operations that are available to specific connections and to restrict access to certain data sets, which improves the security of your data.

You can grant the following permissions:

- **deny**: no access
- **admin**: full access to APIs and documents
- **readwrite**: full access to documents
- **read**: allow only searching and retrieving documents
- **write**: allow updating, adding, and deleting documents

*Note*: Write permission allows the service user to create new indexes that match the pattern, but it does not allow deletion of those indexes.

Rules are defined separately for each user as **pattern/permission** combinations. The **pattern** defines the indexes that the permission applies to. Patterns are glob-style, where * matches any number of characters and ? matches any character.

When multiple rules match, they are applied in the order listed above. If no rules match, access is denied.

#### Controlling access to top-level APIs

OpenSearch has several “top-level” API endpoints (_mget, _msearch, and so on), where you have to grant access separately. To do this, use patterns similar to the index patterns, for example:

- _*/admin would grant unlimited access to all top-level APIs
- _msearch/admin grants unlimited access to the _msearch API only

#### Access control and OpenSearch Dashboards

Enabling ACLs does not restrict access to OpenSearch Dashboards itself, but all requests done by OpenSearch Dashboards are checked against the current user’s ACLs.

In practice, for OpenSearch Dashboards to function properly, you must grant the user admin-level access to the _msearch interface (permission: admin, pattern: _msearch) or switch on the ExtendedAcl option.

## We want your feedback!

We would love to help answer questions and appreciate any feedback you may have.

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](https://www.ovhcloud.com/pt/professional-services/) to get a quote and ask our Professional Services experts for a custom analysis of your project.

Are you on Discord? Connect to our channel at <https://discord.gg/ovhcloud> and interact directly with the team that builds our databases service!
