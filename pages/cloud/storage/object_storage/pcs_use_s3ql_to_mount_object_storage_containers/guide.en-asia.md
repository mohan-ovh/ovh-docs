---
title: Object Storage Swift - Use S3QL to mount object storage containers
slug: pcs/use-s3ql-to-mount-object-storage-containers
section: OpenStack Swift Storage Class Specifics
legacy_guide_number: g1908
order: 160
updated: 2021-10-27
---

**Last updated 27th October 2021**

## Objective

S3QL is a remote file system that can be configured locally to store data using cloud storage solutions like OVH Object Storage.
It has several features, such as data compression, encryption, and container snapshots, which makes this solution particularly suitable for creating backups.

You can find more information directly on their [website](http://www.rath.org/s3ql-docs/).

**This guide shows you how to set up an object container as file system.**

## Prerequisites

- [Configure user](https://docs.ovh.com/asia/en/public-cloud/creation-and-deletion-of-openstack-user/)
- [Add storage space](https://docs.ovh.com/asia/en/public-cloud/create_an_object_container/)

## Instructions

> [!primary]
>
> Using an object container as a file system can impact the performance of your operations.
> S3ql version 3.3 or above is required.
>

### Create your file system

- Create a file containing the login information:

```bash
admin@serveur1:~$ sudo vim s3qlcredentials.txt

[swift]
backend-login: OS_PROJECT_ID:OS_USERNAME
backend-password: OS_PASSWORD
storage-url: swiftks://auth.cloud.ovh.net/REGION_NAME:CT_NAME
fs-passphrase: PASSPHRASE
```

OS_PROJECT_ID, OS_USERNAME and OS_PASSWORD parameters can be found in your OpenRC file.
You can follow this guide below in order to retrieve it: [Access and Security in Horizon](https://docs.ovh.com/asia/en/public-cloud/access_and_security_in_horizon/)

The REGION_NAME and CT_NAME arguments can be adapted according the name and location of your object container.

- Change authentication file access permissions:

```bash
admin@serveur1:~$ sudo chmod 600 s3qlcredentials.txt
```

- Object container formating:

```bash
admin@serveur1:~$ sudo mkfs.s3ql --backend-options domain=default --authfile s3qlcredentials.txt swiftks://auth.cloud.ovh.net/REGION_NAME:CT_NAME
```

You then have to add the passphrase to your authentication file.
If you do not want to configure it, you have to delete the "fs-passphrase: PASSPHRASE" line from your file.


### Configure your file system

- Create the mounting point

```bash
admin@serveur1:~$ sudo mkdir /mnt/container
```

- Mount the object container

```bash
admin@serveur1:~$ sudo mount.s3ql --backend-options domain=default --authfile s3qlcredentials.txt swiftks://auth.cloud.ovh.net/REGION_NAME:CT_NAME /mnt/container/
```

- Check mounting:

```bash
admin@serveur1:~$ sudo df -h

Filesystem Size Used Avail Use% Mounted on
/dev/vda1 9.8G 927M 8.5G 10% /
udev 10M 0 10M 0% /dev
tmpfs 393M 5.2M 388M 2% /run
tmpfs 982M 0 982M 0% /dev/shm
tmpfs 5.0M 0 5.0M 0% /run/lock
tmpfs 982M 0 982M 0% /sys/fs/cgroup
swiftks://auth.cloud.ovh.net/REGION_NAME:CT_NAME 1.0T 0 1.0T 0% /mnt/container
```

You cannot use S3QL in offline mode, you should not configure persistance via the /etc/fstab file but by using a script which will run when your server starts up.

## Go further
  
Join our community of users on <https://community.ovh.com/en/>.