---
title: Overview of supported protocols
slug: protocol-overview
excerpt: Choose yours, no vendor lock-in!
section: Protocol
order: 1
---

**Last updated 23th August, 2019**

### Objective

Metrics is protocol agnostic, it means that you can push your data with OpenTSDB, and query it with Warp 10™ or vice versa.
Metrics doesn't enforce you to a proprietary protocol. Instead, we believe the plurality of existing protocols from Open Source solutions can be used to achieve Pushing and Querying the platform.

### Requirements

- No specific requirement

### Instructions

Each protocol provides different capabilities. Some will be easier than others but may have less features. We've tried to summary them with this simple table :

| Protocol   | Push                         | Query                        | Protocol documentation                                            | Features                                                                          | Corresponding Open Source project                                                                   |
| ---------- | ---------------------------- | ---------------------------- | ----------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| InfluxDB   | <i class="fas fa-check"></i> | <i class="fas fa-check"></i> | [Metrics Influx](../protocol_influxdb/guide.en-gb.md){.ref}       | <i class="fas fa-star"></i>                                                       | [https://docs.influxdata.com/influxdb/v1.7/](https://docs.influxdata.com/influxdb/v1.7/){.external} |
| OpenTSDB   | <i class="fas fa-check"></i> | <i class="fas fa-check"></i> | [Metrics OpenTSDB](../protocol_opentsdb/guide.en-gb.md){.ref}     | <i class="fas fa-star"><i class="fas fa-star">                                    | [http://opentsdb.net/](http://opentsdb.net/){.external}                                             |
| Graphite   | <i class="fas fa-check"></i> | <i class="fas fa-check"></i> | [Metrics Graphite](../protocol_graphite/guide.en-gb.md){.ref}     | <i class="fas fa-star"><i class="fas fa-star"></i>                                | [https://graphiteapp.org/](https://graphiteapp.org/){.external}                                     |
| Metrics2.0 | <i class="fas fa-check"></i> | <i class="fas fa-times"></i> | [Metrics 2.0 spec](../protocol_opentsdb/guide.en-gb.md){.ref}     | <i class="fas fa-star"><i class="fas fa-star">                                    | [http://metrics20.org/](http://metrics20.org/){.external}                                           |
| Prometheus | <i class="fas fa-check"></i> | <i class="fas fa-check"></i> | [Metrics Prometheus](../protocol_prometheus/guide.en-gb.md){.ref} | <i class="fas fa-star"></i><i class="fas fa-star"></i>                            | [https://prometheus.io/](https://prometheus.io/){.external}                                         |
| Warp 10™   | <i class="fas fa-check"></i> | <i class="fas fa-check"></i> | [Metrics Warp 10™](../protocol_warp10/guide.en-gb.md){.ref}       | <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i> | [https://warp10.io/](https://warp10.io/){.external}                                                 |

Most of the protocols don't include **authentification**, so **you need to add the tokens in the Basic Auth field.**

If you're wondering which protocol to choose, here is a simple guideline :

- You want to push json? -> `OpenTSDB`
- You want to instrument your code? -> `Prometheus SDK` & `Beamium`
- You want powerful analytics? -> `Warp 10™` & `WarpScript™`
- You want tooling integration? ->  `InfluxDB`

### Authentification and endpoints

Metrics has builtin security to secure your data. In the [Start section](../metrics_order/guide.en-gb.md){.ref} you've learnt where to get them from the manager. We've generated a default pair of **tokens** :

- a **READ** token to Query
- a **WRITE** token to Push Data

Except for Warp 10™ (where it's provided as a specific Header for push and in the DSL payload for queries), this token will be used as the password in the [Basic Auth](https://en.wikipedia.org/wiki/Basic_access_authentication){.external}.

Most of the protocols are available through HTTPS endpoints. Here's the logic for pushing:

**`https://token:[write token]@[protocol].[region].metrics.ovh.net`**

For example :  https://token:cersX8.P5X_4Zv...LEXV_hoXuKcn_BRp2eqp7@opentsdb.gra1.metrics.ovh.net

The user in the basic authenfication is ignored.

## Go further

- Documentation: [Guides](../product.en-gb.md){.ref}
- Vizualize your data: [https://grafana.metrics.ovh.net/login](https://grafana.metrics.ovh.net/login){.external}
- Community hub: [https://community.ovh.com](https://community.ovh.com/en/c/Platform){.external}
- Create an account: [Try it free!](https://www.ovh.com/fr/order/express/#/new/express/resume?products=~%28~%28planCode~%27metrics-free-trial~configuration~%28~%28label~%27region~values~%28~%27gra1%29%29%29~option~%28~%29~quantity~1~productId~%27metrics%29%29&paymentMeanRequired=0){.external}
