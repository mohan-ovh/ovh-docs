---
title: 'Configuring a new Windows Server installation'
excerpt: 'Find out how to enable Remote Desktop, ICMP and boot logs'
updated: 2023-02-15
---

**Last updated 15th February 2023**

## Objective

After a fresh installation of a Windows Server operating system on a VPS, remote access and the ICMP (Internet Control Message Protocol) response might be disabled. However, you can use the OVHcloud KVM to access your VPS and configure the Windows Firewall application to enable ICMP and allow connections via Remote Desktop Protocol.<br>Activating Windows boot logs can be helpful for server error diagnostics.

**This guide explains how to enable ICMP, Remote Desktop Protocol and boot logs on a Windows VPS.**

## Requirements

- A Windows [VPS](https://www.ovhcloud.com/en/vps/) in your OVHcloud account
- Access to the [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/world/&ovhSubsidiary=we)

## Instructions

### Step 1: Log in with KVM

To access the KVM console of your VPS, please follow the [VPS KVM guide](/pages/bare_metal_cloud/virtual_private_servers/using_kvm_for_vps).

### Step 2: Finish the Windows setup

When the KVM session is established, the initial setup screens will be displayed. Here you need to configure your **country/region**, the **Windows language**, and your **keyboard layout**. Once you have done this, click `Next`{.action}.

![KVM](images/setup-03.png){.thumbnail}

In the second screen, enter a password for your Administrator account and confirm it, then click `Finish`{.action}.

![KVM](images/setup-04.png){.thumbnail}

Windows will apply your settings and then display the Login screen. Click the `Send CtrlAltDel`{.action} button in the top right corner to sign in.

![KVM](images/setup-05.png){.thumbnail}

Enter the password you have previously created for your Administrator account and click on the Arrow button.

![KVM](images/setup-06.png){.thumbnail}

This completes the initial setup. Once logged in, you need to change the appropriate Windows Firewall settings.

### Step 3: Modify Windows Firewall

Open the `Administrative Tools`{.action} of the `System and Security`{.action} control panel and double-click on `Windows Firewall with Advanced Security`{.action}.

![Admin](images/windows4.png){.thumbnail}

Here you can enable the respective `ICMP` and `Remote Desktop` rules (right-click on the rule and select `Enable rule`{.action} in the context menu).

![Enabled](images/windows5.png){.thumbnail}

Your server should now be responding to requests using these protocols.

> [!primary]
> To secure your Windows system with firewall rules, refer to our guide "[Configuring the firewall on Windows](/pages/bare_metal_cloud/virtual_private_servers/activate-port-firewall-soft-win)".
>

### Activating Windows boot logs (optional)

Connect to your server via a Remote Desktop or [KVM](/pages/bare_metal_cloud/virtual_private_servers/using_kvm_for_vps) session. Open the Windows start menu and click on `Run`{.action}.

![Bootlog](images/windowsboot1.png){.thumbnail}

Enter "msconfig" and click on `OK`{.action}.

![Bootlog](images/windowsboot2.png){.thumbnail}

In the new window, check the box next to `Boot log`. Click on `OK`{.action}.

![Bootlog](images/windowsboot3.png){.thumbnail}

The next time your server boots, the logs will be saved into a .txt file. The file path is ```C:\Windows\ntbtlog.txt```.

To access the contents of this file in rescue mode, please follow the instructions in the [VPS rescue mode guide](/pages/bare_metal_cloud/virtual_private_servers/rescue).

## Go further

Join our community of users on <https://community.ovh.com/en/>.
