---
title: VMware vMotion
slug: vmotion-new
routes:
    canonical: 'https://docs.ovh.com/asia/en/private-cloud/vmotion-new/'
excerpt: Find out how to move your virtual machine to a different host (hot migration)
section: VMware vSphere features
order: 4
updated: 2020-11-18
---

**Last updated 18th November 2020**

## Objective

The **vMotion** feature allows you to to perform a hot migration of a (running) virtual machine from a host to another host, resource pool, or Vapp within the same **cluster**.

**This guide explains how to perform this operation.**

## Instructions

### Moving a VM

To move a virtual machine to another resource, right-click on the VM and select `Migrate...`.

![move vm](images/Vmotion1.png){.thumbnail}

### Choosing a migration type

The menu offers several options for vMotion. In this example, the VM is to be migrated to another host. Therefore, select "Change compute resource only".

The option "Change storage only" allows to migrate the VM to another datastore. It is explained in [this guide](../vmware_storage_vmotion/).

![choose vMotion type](images/Vmotion2.png){.thumbnail}

### Choosing a resource

Select a resource to which the virtual machine will be migrated. The VM can be migrated to a host, cluster, resource pool, or Vapp.

In this example, the host with the addresss ending in *.50* is chosen.

![choose resource](images/Vmotion3.png){.thumbnail}

### Choosing the network

In this step, you can choose the network assigned to the VM. In this example, the VM is left on its original VLAN.

![choose network](images/Vmotion4.png){.thumbnail}

### Choosing the priority

It is recommended to perform the migration as a high priority. To do this, select "Schedule vMotion with high priority".

![choose priority](images/Vmotion5.png){.thumbnail}

### Finalising the operation

Click on `FINISH`{.action} to launch the migration task.

![finalise vMotion](images/Vmotion6.png){.thumbnail}

### Tracking the vMotion task

In "Recent Tasks", you can track the migration status. It takes more or less time depending on the assigned RAM, work load and bandwidth used.

![tracking vMotion](images/Vmotion7.png){.thumbnail}

## Go further

Join our community of users on <https://community.ovh.com/en/>.
