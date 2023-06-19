---
title: Deploying cPanel on a VPS'
excerpt: 'Find out how to instantiate a VPS with the pre-installed cPanel application'
updated: 2021-10-14
---

**Last updated 14th October 2021**

## Objective

cPanel is a control panel designed for web hosting. Web hosting tasks are simplified, as it is made up of a graphical interface that allows the automation of settings.

**Learn how to deploy cPanel with pre-installed applications on a VPS.**

## Requirements

- A current [VPS solution](https://www.ovhcloud.com/en-sg/vps/) (VPS ranges Value, Essential, Comfort, or Elite) in your OVHcloud account
- Access to the [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/sg/&ovhSubsidiary=sg)

## Instructions

In order to install your cPanel server, you will first need to order a VPS with a cPanel distribution.

![horizon](images/cpanel_order.png){.thumbnail}

When your VPS is ready, you will receive an email providing the information to connect to your cPanel server:

>Your application(s):
>
>You can connect to cPanel from https://*hostname*:2087/*session_parameters*

If you already have a VPS and want to have cPanel on it, you can reinstall the VPS from your [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/sg/&ovhSubsidiary=sg) with the "CentOS 7 - cPanel" template (available only with a compatible VPS solution).

> [!warning]
>
> If you reinstall a VPS, all data stored on the VPS will be lost.
>


### First connection

Once you received the email with the unique link, please proceed to the link to do the initial setup. 

> [!primary]
>
> If the link has expired already, please connect to your VPS via SSH using the CentOS user and execute the “sudo whmlogin” command to generate a new link.
>

The URL above allows you to log in without credentials (user and password) to your WHM manager.

#### Step 1: Read and accept the terms of cPanel

![horizon](images/license_validation.png){.thumbnail}

#### Step 2: Provide your email and nameservers you wish to set on the VPS

![horizon](images/setup_config_cpanel.png){.thumbnail}

#### Step 3: Set the root password

![horizon](images/change_root.png){.thumbnail}

Now you should be able to login to WHM and SSH using the root user with the password that was just set.

### Securing your service

We recommend that you take further additional steps to ensure you secure your WHM and VPS. For this we recommend reading the recommendations provided by cPanel [here](https://docs.cpanel.net/knowledge-base/security/tips-to-make-your-server-more-secure/).

Furthermore we recommend setting up the [OVHcloud network firewall](/pages/cloud/dedicated/firewall_network) and [set up a backup solution](/pages/cloud/vps/secure_your_vps#backing-up-your-system-and-your-data) on your VPS.

## Go further

Join our community of users on <https://community.ovh.com/en/>.
