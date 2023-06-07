---
title: Mount your HA-NAS on Windows Server via CIFS
excerpt: This guide shows you how to mount your HA-NAS on Windows Server via CIFS.
updated: 2021-11-22
---

**Last updated 22nd November 2021**

## Objective

Configure and mount an OVHcloud HA-NAS storage space on your Windows Server using CIFS.

## Requirements

- a [Dedicated Server](https://www.ovhcloud.com/en-ie/bare-metal/) **or** a [VPS](https://www.ovhcloud.com/en-ie/vps/) **or** a [Public Cloud Instance](https://www.ovhcloud.com/en-ie/public-cloud/) with a Windows distribution
- a [HA-NAS solution](https://www.ovh.ie/nas/)

### Settings

- **Windows Server 2008**: Click on the menu `Start`{.action} > `All the programs`{.action} > `Accessories`{.action} > `Command prompt`{.action}.
- **Windows Server 2012**: Click the `Windows PowerShell`{.action} icon at the bottom of the screen in the taskbar.
- **Windows Server 2016**: Click on the menu `Start`{.action}, then on the `Windows PowerShell`{.action} icon.
- **Windows Server 2019**: Click on the menu `Start`{.action}, then on the `Windows PowerShell`{.action} icon.

Then run the following command:

```bash
net use z: \\CIFS_SERVER_IP\CIFS_PATH
```

### Example

- CIFS mounting for a NAS-HA:

```bash
net use z: \\10.16.101.8\zpool-000206_PARTITION_NAME_1
```

> [!alert]
>
> The SMB/CIFS user is `nobody`. Changing permissions with this user may generate conflicts with existing NFS permissions. 
> 

## Go further

[NAS - Frequently Asked Questions](/pages/cloud/storage/file_storage/nas_faq)

Join our community of users on <https://community.ovh.com/en/>.
