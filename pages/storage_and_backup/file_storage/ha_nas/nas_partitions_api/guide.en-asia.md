---
title: HA-NAS - Managing partitions via API
excerpt: Find out how to manage HA-NAS partitions using the OVHcloud API
updated: 2022-07-20
---

**Last updated 20th July 2022**

## Objective

The OVHcloud HA-NAS service allows you to manage file storage that can be accessed over a network.

**This guide explains how to manage the partitions of your HA-NAS service via the OVHcloud API.**

## Requirements

- An OVHcloud [HA-NAS service](https://www.ovh.co.uk/nas/)
- Consulting the [OVHcloud API first steps guide](/pages/manage_and_operate/api/first-steps) to familiarise yourself with the OVHcloud APIv6

## Instructions

All API routes in this guide are available in the section */dedicated/nasha*: <https://api.ovh.com/console/#/dedicated/nasha>.

> [!primary]
>
> When using the API, all fields marked with an asterisk (\*) are required.
>

### Retrieving information about your service

All your active services can be retrieved by using the following route:

> [!api]
>
> @api {GET} /dedicated/nasha
>

### Listing all partitions

Use the following route to retrieve the partitions of a service:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {GET} /dedicated/nasha/{serviceName}/partition
>> >
>>
>
> Parameters:
>
>> > **serviceName** *
>> >
>> >> The internal name of your HA-NAS service
>

### Retrieving the properties of a partition

To view the details of a partition, use the following route:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {GET} /dedicated/nasha/{serviceName}/partition/{partitionName}
>> >
>>
>
> Parameters:
>
>> > **serviceName** *
>> >
>> >> The internal name of your HA-NAS service
>> >
>> > **partitionName** *
>> >
>> >> Name of the partition
>

### Retrieving statistics for a partition

Use the following route to retrieve usage information for a partition:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {GET} /dedicated/nasha/{serviceName}/partition/{partitionName}/use
>> >
>>
>
> Parameters:
>
>> > **serviceName** *
>> >
>> >> The internal name of your HA-NAS service
>> >
>> > **partitionName** *
>> >
>> >> Name of the partition
>> >
>> > **type** *
>> >
>> >> The type of statistic to be fetched: *size*, *used* or *usedbysnapshots*
>

### Creating a partition

Use the following route to create a new partition:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {POST} /dedicated/nasha/{serviceName}/partition
>> >
>>
>
> Parameters:
>
>> > **serviceName** *
>> >
>> >> The internal name of your HA-NAS service
>> >
>> > **partitionDescription** 
>> >
>> >> Optional description
>> >
>> > **partitionName** *
>> >
>> >> A name for the partition
>> >
>> > **protocol** *
>> >
>> >> *NFS*, *CIFS*, or *NFS_CIFS* for both 
>> >
>> > **size** *
>> >
>> >> The size of the partition
>

Choose `NFS` as protocol and a size of `10` Gigabytes, for example.

### Modifying the properties of a partition

Use the following route to alter a partition:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {PUT} /dedicated/nasha/{serviceName}/partition/{partitionName}
>> >
>>
>
> Parameters:
>
>> > **serviceName** *
>> >
>> >> The internal name of your HA-NAS service
>> >
>> > **partitionName** *
>> >
>> >> Name of the partition
>> >
>> > **partitionDescription**
>> >
>> >> The new description
>> >
>> > **size**
>> >
>> >> The new size of the partition
>

### Retrieving the ZFS settings of a partition

Use the following route to retrieve the ZFS settings:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {GET} /dedicated/nasha/{serviceName}/partition/{partitionName}/options
>> >
>>
>
> Parameters:
>
>> > **serviceName** *
>> >
>> >> The internal name of your HA-NAS service
>> >
>> > **partitionName** *
>> >
>> >> Name of the partition
>

### Changing the ZFS settings of a partition

> [!warning]
>
> All the default Z File System settings are optimised. We do not recommend changing these parameters.
>

Use the following route to edit the ZFS settings:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {POST} /dedicated/nasha/{serviceName}/partition/{partitionName}/options
>> >
>>
>
> Parameters:
>
>> > **serviceName** *
>> >
>> >> The internal name of your HA-NAS service
>> >
>> > **partitionName** *
>> >
>> >> Name of the partition
>> >
>> > **atime**
>> >
>> >> Access time update setting: *on* (default) or *off*
>> >
>> > **recordsize**
>> >
>> >> Maximum block size: *131072* (default), *16384*, *32768*, *4096*, *65536*, or *8129*
>> >
>> > **sync**
>> >
>> >> File synchronisation setting: *always*, *disabled*, or *standard* (default)
>


### Deleting a partition

Use the following route to delete a partition:

> [!faq]
>
> API:
>
>> > [!api]
>> >
>> > @api {DELETE} /dedicated/nasha/{serviceName}/partition/{partitionName}
>> >
>>
>
> Parameters:
>
>> > **serviceName** *
>> >
>> >> The internal name of your HA-NAS service
>> >
>> > **partitionName** *
>> >
>> >> Name of the partition
>

## Go further

[Mount your NAS via NFS share](/pages/storage_and_backup/file_storage/ha_nas/nas_nfs)

[Mount your NAS on Windows Server via CIFS](/pages/storage_and_backup/file_storage/ha_nas/nas_cifs)

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](https://www.ovhcloud.com/asia/professional-services/) to get a quote and ask our Professional Services experts for assisting you on your specific use case of your project.

Join our community of users on <https://community.ovh.com/en/>.