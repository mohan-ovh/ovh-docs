---
title: Redis - Connectez-vous avec Python (EN)
excerpt: Connect to your Public Cloud Databases for Redis using the Python programming language
updated: 2022-03-24
---

## Objective

Public Cloud Databases allow you to focus on building and deploying cloud applications while OVHcloud takes care of the database infrastructure and maintenance in operational conditions.

**This guide explains how to connect to a Redis database instance with one of the world's most famous programming language: Python.**

You can find an example on the [Github examples repository](https://github.com/ovh/public-cloud-databases-examples/tree/main/databases/redis/python/hello-world).

## Requirements

- Access to the [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/fr/&ovhSubsidiary=qc)
- A [Public Cloud project](https://www.ovhcloud.com/fr-ca/public-cloud/) in your OVHcloud account
- A Redis database running on your OVHcloud Public Cloud Databases ([this guide](/pages/public_cloud/public_cloud_databases/databases_01_order_control_panel) can help you to meet this requirement)
- [Configure your Redis instance](/pages/public_cloud/public_cloud_databases/redis_08_prepare_for_incoming_connections) to accept incoming connections
- A PHP environment with a stable version and public network connectivity (Internet). This guide was made in PHP 7.4.

## Concept

A Redis instance can be managed through multiple ways.
One of the easiest, yet powerful, is to use a Command Line Interface (CLI), as shown in our guide : [Connect to Redis with CLI](/pages/public_cloud/public_cloud_databases/redis_03_connect_cli).

Another way is to interact directly using programming languages, such as Python.

We will need to set up our Python environment with redis-py client, then code in Python to perform a few example actions.

## Instructions

### Set up your Python environment

To interact with your Redis instance using Python, your development environment needs to be configured with:

- A compatible version of Python
- Redis-py

Please follow the official [Redis-py](https://github.com/redis/redis-py#installation){.external} to get the latest information.

Once your Python environment is set up and you begin executing a **python --version** in your command line interface (CLI), you should see information about the version as shown below :

```python
laptop$ python3 --version
Python 3.9.7
```

In the same console, by typing a **pip list**, check if **redis-py** is correctly installed :

```python
laptop$  pip list
Package                Version
---------------------- -------
(...)
redis                  4.2.0
(...)
```

We are now ready to learn how to connect to our Redis instance !

### Connect with redis-py

In your PHP environment, let's try a connection. To be sure that we are indeed connected, set a data pair and then check we can get the value of it.

*redis-connect.py*

```python
import redis
r = redis.Redis.from_url( url='rediss://redisUser:6D74VEUdiLb3XMzE@redis-0d42e4a5-o2626ab53.database.cloud.ovh.net:20185')
r.set("foo","bar")
print(r.get("foo"))
```

```bash
$ python redis-connect.py
$ b'bar'
```

Congratulations! Everything is working properly.

## Go further

Visit our dedicated Discord channel: <https://discord.gg/ovhcloud>. Ask questions, provide feedback and interact directly with the team that builds our databases services.

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](https://www.ovhcloud.com/fr-ca/professional-services/) to get a quote and ask our Professional Services experts for a custom analysis of your project.

Join our community of users on <https://community.ovh.com/en/>.
