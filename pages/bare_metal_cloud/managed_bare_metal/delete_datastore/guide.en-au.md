---
title: 'Removing a datastore'
routes:
    canonical: '/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/delete_datastore'
excerpt: 'Find out how to remove a datastore from your Managed Bare Metal'
legacy_guide_number: '7766789'
updated: 2020-11-18
---

## Objective

In certain cases — like replacing a datastore or scaling it up to a higher capacity, for example — it may be useful to remove a datastore from your cluster.

**This guide will show you how to securely remove a datastore from your infrastructure.**

## Requirements

* an [OVHcloud Managed Bare Metal](https://www.ovhcloud.com/en-au/managed-bare-metal/){.external} solution
* access to the vSphere management interface

## Instructions

> [!warning]
>
> Please note that you cannot remove the  **two 300 GB or 1.2 TB datastores** included in your pack. For security reasons, the removal request will also be blocked if you have virtual machines (VMs) on the datastore concerned (they will be listed in the confirmation window).
> 

To remove a datastore, right-click on the resource concerned. Then select `OVHcloud`{.action}, and `Remove this Storage`{.action}.

![Choice of datastore](images/removedatastore01.png){.thumbnail}

A confirmation window will pop up. Confirm by clicking `Next`{.action}.

![Confirm removal](images/removedatastore02.png){.thumbnail}

The removal request will then be processed.

![Removal confirmed](images/removedatastore03.png){.thumbnail}

You can also monitor the progress of the datastore removal in `Recent Tasks`{.action}.

![Removal monitoring task](images/removedatastore04.png){.thumbnail}

## Go further

Join our community of users on <https://community.ovh.com/en/>.
