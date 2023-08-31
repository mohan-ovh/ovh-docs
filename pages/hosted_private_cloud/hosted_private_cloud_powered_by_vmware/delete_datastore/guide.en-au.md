---
title: 'Removing a datastore'
excerpt: 'Find out how to remove a datastore from your Private Cloud'
legacy_guide_number: '7766789'
updated: 2020-07-01
---

## Objective

In certain cases — like replacing a datastore or scaling it up to a higher capacity, for example — it may be useful to remove a datastore from your cluster.

**This guide will show you how to securely remove a datastore from your infrastructure.**

## Requirements

* an [OVHcloud Hosted Private Cloud](https://www.ovhcloud.com/en-au/enterprise/products/hosted-private-cloud/){.external} solution
* access to the vSphere management interface

## Instructions

> [!warning]
>
> For security reasons, the removal request will be blocked if you have virtual machines (VMs) on the datastore concerned (they will be listed in the confirmation window).
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
