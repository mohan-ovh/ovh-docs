---
title: 'Use InfluxDB'
slug: protocol-influxdb
excerpt: 'Get an overview on how to use InfluxDB for Metrics'
section: Protocol
order: 4
---

**Last updated 26 April, 2019**

## Objective

InfluxDB is a proprietary time series database that integrates with [Telegraf](https://github.com/influxdata/telegraf){.external}. In this guide, you will learn how to push using the Influx protocol with Metrics.

## Requirements

- a valid OVH Metrics account.

## Instructions

### Compatibility

| API    | Method | Supported                    |
| ------ | ------ | ---------------------------- |
| /write | POST   | <i class="fas fa-check"></i> |

InfluxDB has the notion of databases. This concept doesn't exist within Metrics. If you need segmentation, you can use different Metrics project or isolate with an additional label.

Metrics currently doesn't support Influx Query Language.

### Data Model

InfluxDB uses it own data model :

```txt
 <measurement>[,<tag_key>=<tag_value>[,<tag_key>=<tag_value>]] <field_key>=<field_value>[,<field_key>=<field_value>] [<timestamp>]
```

### How to push data

> The full documentation is available at [https://docs.influxdata.com/influxdb/v1.2/guides/writing_data/](https://docs.influxdata.com/influxdb/v1.2/guides/writing_data/){.external}

#### Authentification

To push data to the platform, you will need a **WRITE TOKEN**. Use Basic Auth directly inside the URL to pass it properly, like this :

<pre>https://metrics:[WRITE_TOKEN]@influxdb.[region].metrics.ovh.net</pre>

#### Pushing datapoints using curl

```sh
 curl -i -XPOST \
     'https://DESC:TOKEN_WRITE@influxdb.gra1.metrics.ovh.net/write' \
     --data-binary \
     'cpu_load_short,host=server01,region=us-west value=0.64 1434055562000000000'
```

### How to query data

InfluxDB has its own Query DSL, that mimics SQL without being plain ANSI SQL.

```sql
 SELECT <field_key>[,<field_key>,<tag_key>] FROM <measurement_name>[,<measurement_name>]
```

Metrics currently doesn't support Influx Query Language.

## Going further

You can learn how to configure a Grafana datasource by following [this guide](../start-grafana).

You can also exchange with our community of users on [https://community.ovh.com](https://community.ovh.com){.external}.
