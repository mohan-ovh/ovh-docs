---
title: PostgreSQL - Capacités et limitations (EN)
slug: postgresql/capabilities
excerpt: Discover the capabilities and limitations of Public Cloud Databases for PostgreSQL
section: PostgreSQL - Guides
order: 1
routes:
    canonical: 'https://docs.ovh.com/gb/en/publiccloud/databases/postgresql/capabilities/'
---

**Last updated January 26<sup>th</sup>, 2022**

## Objective

This page provides the technical capabilities and limitations of the Public Cloud Databases for PostgreSQL offer.
We improve our offers continuously. You can follow and submit ideas to add to our roadmap at <https://github.com/ovh/public-cloud-roadmap/projects/2>.

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

- PostgreSQL 10
- PostgreSQL 11
- PostgreSQL 12
- PostgreSQL 13
- PostgreSQL 14

You can folllow EOL lifecycle for PostgreSQL version on their official page : <https://www.postgresql.org/support/versioning/>

### PostgreSQL connectors

You can use any of the [PostgreSQL-recommended drivers and extensions](https://www.postgresql.org/download/product-categories/){.external} to access your instance.

### Plans

Three plans are available:

- *Essential*
- *Business*
- *Enterprise*

Here is an overview of the various plans capabilities:

| Plan         | Number of nodes by default | Read replicas | Network                |
| ------------ | -------------------------- | ------------- | ---------------------- |
| *Essential*  | 1                          | No            | Public only            |
| *Business*   | 2                          | Planned       | Public & Private vRack |
| *Enterprise* | 3                          | Planned       | Public & Private vRack |

Your choice of plan affects the number of nodes your cluster can run, the SLA, and a few other features such as private network, read replicas and backup retention.

#### Nodes and replicas

- **Essential**: the cluster can support at most one node.
- **Business**: the cluster is delivered with 2 nodes by default. Adding read replicas is planned.
- **Enterprise**: the cluster is delivered with 3 nodes by default. Adding read replicas is planned.

#### License type

PostgreSQL software is under the PostgreSQL License, a liberal open-source license, similar to BSD or MIT licenses.
More information on <https://www.postgresql.org/about/licence/>.

### Hardware resources

Here are the node types you can choose from:

| Name    | Disk (GB) | Cores | Memory (GB) |
| ------- | --------- | ----- | ----------- |
| db1-7   | 160       | 2     | 7           |
| db1-15  | 320       | 4     | 15          |
| db1-30  | 640       | 8     | 30          |
| db1-60  | 1280      | 16    | 60          |
| db1-120 | 2560      | 32    | 120         |

Right now, all nodes of a given cluster should be of the same type and distributed in the same region.

#### Effective storage

The disk size listed above is the total disk size of the underlying machine. However, a small part of it goes towards the OS install.

We try hard to avoid "disk full" situations that could be harmful to cluster health. Therefore:

1. When reaching 97% capacity, the customer will have his database instance moved in "DISK_FULL" state, and "read-only" mode, meaning no more writes can be done.
2. You then have the ability to upgrade to a higher service plan with more storage.

### Features

#### Network

PostgreSQL clusters are reachable through default port 5432.

Public networking can be used for all the offers.

Private networking (vRack) is planned for *Business* and *Enterprise*.

When using private networking, some network ports get created in the private network of your choice. Thus, further operations on that network might suffer from some restrictions - e.g. you won't be able to delete the network if you didn't stop the Public Cloud Databases services first.

Ingress and Egress traffic are included in the service plans and unmetered.

#### Maximum simultaneous connections

The number of simultaneous connections in Public Cloud Databases for PostgreSQL depends on the available total memory on the node.
We allow approximately 100 connections per 4 GB of RAM memory, capped to a maximum of 1000 active connections.

So for example on a server with 7 GB memory, you will get approximately 200 connections and with 15 GB memory you will get 400 connections.

#### Advanced parameters

We do not currently support PostgreSQL advanced parameters.

#### Backups

*Essential* plan clusters are automatically backed up daily during their maintenance window. Backup retention is 2 days.

*Business* plan clusters are automatically backed up daily during their maintenance window. Backup retention is 14 days.

*Enterprise* plan clusters are automatically backed up daily during their maintenance window. Backup retention is 30 days.

#### Logs and metrics

Logs and metrics are available via the OVHcloud Public Cloud Control Panel.
As of today, you can't export logs and metrics, nor plug them into a remote tool.

- **Logs retention :** 1000 lines of logs;
- **Metrics retention :** 1 calendar month.

Please note that if the database instance is deleted, logs and metrics are also automatically deleted.

#### Users and roles

Creation of users is allowed via the Control Panel and API with default admin roles and privileges.
You can't select specific privileges.

## We want your feedback!

We would love to help answer questions and appreciate any feedback you may have.

Are you on Discord? Connect to our channel at <https://discord.gg/PwPqWUpN8G> and interact directly with the team that builds our databases service!
