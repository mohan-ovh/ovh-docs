---
title: Cluster status
excerpt: This guide shows you how to check your Ceph cluster status and health.
updated: 2020-12-22
---

**Last update 22nd December 2020**


## Using web interface
First, connect to the [Cloud Disk Array manager](https://www.ovh.com/manager/cloud/index.html){.external}. Under 'Platforms and services' select your Ceph cluster. You will see two differents parts: **cluster details** and **cluster health**.


### Cluster details

![Ceph users](images/check_cluster_status_1.png){.thumbnail}

Additional explanations:


> [!faq]
>
> **Label**
>>
>> Name given to you cluster
>>
>>
> **Region**
>>
>> We currently deliver Ceph clusters on Strasbourg, Gravelines and Beauharnois.
>>
>>
> **Version**
>>
>> We currently deliver clusters up to version 9.2.1 ([official Ceph releases](https://docs.ceph.com/en/latest/releases/general/){.external})
>>
>>
> **Tunable**
>>
>> It's the algorithm used to place datas.
>>
>>
> **Status**
>>
>> Installed means that all tasks requested are done.
>>
>>
> **State**
>>
>> Active
>>
>>
> **Monitors**
>>
>> IP that you have to use to reach your monitors.
>>
>>
> **Create date**
>>
>> Creation date of your cluster
>>
>>
> **Update date**
>>
>> Date of the last task applied to your cluster
>>
>>
>

### Cluster health

![Ceph users](images/check_cluster_status_2.png){.thumbnail}

Additional explanations:


> [!faq]
>
> **Status**
>>
>> HEALTH_OK means that every objects are at the right place and have 3 replicates.
>>
>>
>> HEALTH_WARN means that some objects are missplaced (like after a growth) or that some object are not replicated three times. In this case cluster is recovering
>>
>>
> **Healthy**
>>
>> Boolean indicating if everything is ok with Ceph cluster or not
>>
>>
> **Availables bytes**
>>
>> Free bytes available in the cluster (before replication)
>>
>>
> **Used bytes**
>>
>> Bytes currently used in the cluster (after replication)
>>
>>
> **Space usage [%]**
>>
>> Percentage of *used bytes* in relation to *total bytes*
>>
>>
> **Cluster active tasks**
>>
>> List of user-initiated tasks that are currently being processed for this cluster
>>
>>
>

## Using API
Get Ceph cluster details with a simple HTTP call.


> [!api]
>
> @api {GET} /dedicated/ceph/{serviceName}
>
Example:


```bash
GET /dedicated/ceph/98d166d8-7c88-47b7-9cb6-63acd5a59c15
{
  updateDate: "2016-07-26T09:16:07"
  status: "INSTALLED"
  region: "SBG1"
  serviceName: "98d166d8-7c88-47b7-9cb6-63acd5a59c15"
  state: "ACTIVE"
  createDate: "2016-07-20T08:00:37"
  cephMons: [
    "10.99.187.210"
    "10.99.191.210"
    "10.97.131.210"
  ]
  crushTunables: "OPTIMAL"
  label: "Ceph cluster"
  cephVersion: "9.2.1"
}
```

Get Ceph cluster health:


> [!api]
>
> @api {GET} /dedicated/ceph/{serviceName}/health
>

```bash
{
  status: "HEALTH_OK"
  availableBytes: 5891996504064
  serviceName: "98d166d8-7c88-47b7-9cb6-63acd5a59c15"
  healthy: true
  usedBytes: 124981248
}
```

## Go further

Visit our dedicated Discord channel: <https://discord.gg/ovhcloud>. Ask questions, provide feedback and interact directly with the team that builds our Storage and Backup services.

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](https://www.ovhcloud.com/en-ie/professional-services/) to get a quote and ask our Professional Services experts for assisting you on your specific use case of your project.


Join our community of users on <https://community.ovh.com/en/>.
