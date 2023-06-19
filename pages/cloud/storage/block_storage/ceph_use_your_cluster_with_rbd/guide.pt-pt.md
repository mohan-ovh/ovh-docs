---
title: Acesse o cluster usando o cliente rbd (EN)
excerpt: This guide shows you how to access your cluster using rbd client.
routes:
    canonical: '/pages/cloud/storage/block_storage/ceph_use_your_cluster_with_rbd'
updated: 2022-06-22
---

**Last update 22th June 2022**

## Objective

There are different ways to use your Ceph cluster. We'll describe how to map your cluster using **rbd client**.

## Requirements

You must first ensure that you have done those steps :

- [Create a pool](/pages/cloud/storage/block_storage/ceph_create_a_pool)
- [Create a user](/pages/cloud/storage/block_storage/ceph_create_a_user)
- [Add rights to a user on a pool](/pages/cloud/storage/block_storage/ceph_change_user_rights)
- [Add an IP ACL](/pages/cloud/storage/block_storage/ceph_create_an_ip_acl) to allow your server to contact the cluster


## Ceph installation
For **deb based** distributions:


```bash
ubuntu@server:~$ sudo apt-get -y install ceph ceph-common
[...]
Setting up ceph-common (10.2.0-0ubuntu0.16.04.2) ...
Setting up ceph (10.2.0-0ubuntu0.16.04.2) ...
```

For **rpm based** distributions:


```bash
[centos@server ~]$ sudo yum install -y ceph-common
[...]
Installed:
ceph-common.x86_64 1:0.80.7-3.el7
```


## Ceph configuration
Create file `/etc/ceph/ceph.conf`


```ini
[global]
mon_host = <mon_1_IP>,<mon_2_IP>,<mon_3_IP>
```

Create the file `/etc/ceph/ceph.client.<ceph_user_name>.keyring`


```ini
[client.<ceph_user_name>]
key = <my_user_key>
```

`<mon_X_IP>` has to be replaced by monitors IP you can find on the [Cloud Disk Array manager](https://ca.ovh.com/manager/){.external}. Under 'Platforms and services' select your Ceph cluster.

`<my_user_key>` has to be replaced by the users's key you can find on your Cloud Disk Array manager.


## Configuration check
You can check the configuration by listing the images inside your pool.


```bash
ubuntu@server:~$ rbd -n client.myuser list mypool
```

In this case, the result is empty because we have not have created an image yet. If you have an error, please double check your configuration.


## Image creation
You can't directly mount a pool, you have to **mount an image** that exists on the pool.


```bash
ubuntu@server:~$ rbd -n client.myuser create mypool/myimage -s $((10*1024*1024)) --image-format 2 --image-feature layering
ubuntu@server:~$ rbd -n client.myuser list mypool
myimage
```

We make sure that the image was created correctly by listing the pool content.


## Map the image

```bash
ubuntu@server:~$ sudo rbd -n client.myuser map mypool/myimage
/dev/rbd0
```

My rbd image is not mapped to /dev/rbd0, it's a block storage. Therefore we have to **setup a filesystem**.


## Setup the filesystem

```bash
ubuntu@server:~$ sudo mkfs.xfs /dev/rbd0
meta-data=/dev/rbd0              isize=512    agcount=33, agsize=83885056 blks
         =                       sectsz=512   attr=2, projid32bit=1
         =                       crc=1        finobt=1, sparse=0
data     =                       bsize=4096   blocks=2684354560, imaxpct=5
         =                       sunit=1024   swidth=1024 blks
naming   =version 2              bsize=4096   ascii-ci=0 ftype=1
log      =internal log           bsize=4096   blocks=521728, version=2
         =                       sectsz=512   sunit=8 blks, lazy-count=1
realtime =none                   extsz=4096   blocks=0, rtextents=0
```


## Mount the filesystem

```bash
ubuntu@server:~$ sudo mkdir /mnt/rbd
ubuntu@server:~$ sudo mount /dev/rbd0 /mnt/rbd
ubuntu@server:~$ df -h /mnt/rbd
Filesystem      Size  Used Avail Use% Mounted on
/dev/rbd0        10T   34M   10T   1% /mnt/rbd
```

You can now use your Ceph cluster!

## Go further

Visit our dedicated Discord channel: <https://discord.gg/ovhcloud>. Ask questions, provide feedback and interact directly with the team that builds our Storage and Backup services.

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](https://www.ovhcloud.com/pt/professional-services/) to get a quote and ask our Professional Services experts for assisting you on your specific use case of your project.


Join our community of users on <https://community.ovh.com/en/>.
