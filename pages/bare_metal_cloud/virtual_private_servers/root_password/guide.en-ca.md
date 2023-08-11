---
title: Changing your root password on a VPS
excerpt: Find out how to change the root or admin password of a VPS
updated: 2023-06-26
---

## Objective

It may become necessary to change the root password on your GNU/Linux operating system. There are two possible scenarios:

- You are still able to log in via SSH.
- You are unable to log in via SSH because you have lost your password.

**This guide will explain how to proceed with changing your admin password depending on the initial situation.**

## Requirements

- An OVHcloud [VPS](https://www.ovhcloud.com/en-ca/vps/) already set up
- Login credentials received via email after the installation (if still valid)
- Access to the [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/en/&ovhSubsidiary=ca) (for using rescue mode)

> [!warning]
>OVHcloud is providing you with services for which you are responsible, with regard to their configuration and management. You are therefore responsible for ensuring they function correctly.
>
>This guide is designed to assist you in common tasks as much as possible. Nevertheless, we recommend that you contact a [specialist service provider](https://partner.ovhcloud.com/en-ca/directory/) if you have difficulties or doubts concerning the administration, usage or implementation of services on a server.
>

## Instructions

### Changing the password if you still have access (sudo user or root)

> [!primary]
>
> For more information about connecting to your VPS, please consult the [first steps guide](/pages/bare_metal_cloud/virtual_private_servers/starting_with_a_vps).
>

Log in to your VPS via SSH. Switch to the root user, if necessary:

```bash
sudo su -
#
```

Change the password of the current user:

```bash
passwd

New password:
Retype new password:
passwd: password updated successfully
```

> [!primary]
>
> On a GNU/Linux distribution, the password you enter **will not appear**.
>

If you need to permit logging in as root, follow the steps in [this guide section](./#enabling-root-login).

### Changing the password if you have lost it

<iframe width="560" height="315" src="https://www.youtube.com/embed/ua1qoTMq35g?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

#### Step 1: Restart the VPS into rescue mode

Log in to your [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/en/&ovhSubsidiary=ca) and reboot the VPS in rescue mode.
Find further instructions about activating rescue mode with a VPS in our [rescue mode guide](/pages/bare_metal_cloud/virtual_private_servers/rescue).

#### Step 2: Identify the mount point

On legacy VPS ranges, your partitions will be automatically mounted in rescue mode. You can use the following commands to verify this and identify where your partition is mounted:

##### **df -h**

```bash
df -h
```

```console
Filesystem      Size  Used Avail Use% Mounted on
udev            5.8G     0  5.8G   0% /dev
tmpfs           1.2G   17M  1.2G   2% /run
/dev/sda1       2.4G  1.5G  788M  66% /
tmpfs           5.8G     0  5.8G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           5.8G     0  5.8G   0% /sys/fs/cgroup
/dev/sdb1        49G  1.2G   48G   3% /mnt/sdb1
/dev/sdb15      105M  3.6M  101M   4% /mnt/sdb15
```

##### **lsblk**

```bash
lsblk
```

```console
NAME    MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda       8:0    0  2.5G  0 disk
└─sda1    8:1    0  2.5G  0 part /
sdb       8:16   0   50G  0 disk
├─sdb1    8:17   0 49.9G  0 part /mnt/sdb1
├─sdb14   8:30   0    4M  0 part
└─sdb15   8:31   0  106M  0 part /mnt/sdb15
```

The example output above shows that the system partition is mounted on **/mnt/sdb1**.

If your VPS is of the current ranges, the `MOUNTPOINT` column should be empty. In that case, mount the partition first:

```bash
mkdir -p /mnt/sdb1
mount /dev/sdb1 /mnt/sdb1
```

#### Step 3: CHROOT permissions

You now need to edit the root directory to apply the changes to your system. You can do this by using the `chroot` command:

```bash
chroot /mnt/sdb1/
```

You can check by typing the `ls -l` command, which will list the content stored in the current directory of your system:

```bash
ls -l
```

#### Step 4: Change the (root) password

In the last step, change your password with the `passwd` command.

```bash
passwd

New password:
Retype new password:
passwd: password updated successfully
```

If your VPS is of the current ranges (naming scheme: *vps-XXXXXXX.vps.ovh.net*), you have initially received login credentials for a user with elevated permissions instead of the default "root" account. Additionally, the SSH service is not accepting login requests as root.

It is therefore necessary to enter the username you actually use to log in after `passwd`:

```bash
passwd username
New password:
Retype new password:
passwd: password updated successfully
```

This will ensure that you can log in again with this username after rebooting, in case root login is disabled.

Finally, reboot your VPS in 'normal' mode in your [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/en/&ovhSubsidiary=ca).


### Enabling root login <a name="enableroot"></a>

If your VPS is of the current ranges (naming scheme: *vps-XXXXXXX.vps.ovh.net*), you have received login credentials for a user with elevated permissions instead of the default "root" account. Additionally, the SSH service is not accepting login requests as root.

> [!warning]
>
> Enabling root logins is usually regarded as a security vulnerability and is therefore not recommended.
>
> We recommend taking measures to secure your VPS first. You can refer to our guide on [Securing a VPS](/pages/bare_metal_cloud/virtual_private_servers/secure_your_vps).
>

#### Step 1: Edit the sshd_config file

Use a text editor such as vim or nano to edit this configuration file:

```bash
sudo nano /etc/ssh/sshd_config
```

Add the following line.

```text
PermitRootLogin yes
```

Look for this line and make sure it is still commented out:

```text
#PermitRootLogin prohibit-password
```

Save the file and exit the editor.

#### Step 2: Restart the SSH service

You should be able to restart the SSH service with one of the following commands:

```bash
sudo systemctl restart ssh
```

```bash
sudo systemctl restart sshd
```

This should be sufficient to apply the changes. Alternatively, reboot the VPS (`~$ sudo reboot`).

### Troubleshooting

If you encounter boot issues after you have changed your password and initiated the reboot:

- Check the KVM for important information as to why the VPS is unable to start. Consult the [KVM guide](/pages/bare_metal_cloud/virtual_private_servers/using_kvm_for_vps) for help using this feature in the OVHcloud Control Panel.
- If the KVM is showing the VPS booting or unable to find the disk, ensure you have [boot logs enabled](/pages/bare_metal_cloud/virtual_private_servers/bootlog_display_kvm). Relay the pertinent logs to our support teams by creating a support request in your [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/en/&ovhSubsidiary=ca) for further investigations.

## Go further

[Introduction to SSH](/pages/bare_metal_cloud/dedicated_servers/ssh_introduction)

[Securing a VPS](/pages/bare_metal_cloud/virtual_private_servers/secure_your_vps)

Join our user community on <https://community.ovh.com/en/>.