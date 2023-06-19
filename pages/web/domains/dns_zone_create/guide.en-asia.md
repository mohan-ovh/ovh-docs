---
title: 'Creating an OVHcloud DNS zone for a domain name'
excerpt: 'Find out how to create an OVHcloud DNS zone for your domain name via the OVHcloud Control Panel'
updated: 2018-08-06
---

**Last updated 8th February 2023**

## Objective

A Domain Name System (DNS) zone is a domain name’s config file. It is composed of technical information, otherwise called ‘records’. DNS zones are usually used to link your domain name to the server (or servers) that host your website and email addresses.

For a number of reasons, you may need to create a DNS zone for your domain name at OVHcloud.

**Find out how to create an OVHcloud DNS zone for your domain name via the OVHcloud Control Panel.**

## Requirements

- A domain name that does not already have an OVHcloud DNS zone, and is not part of an operation or order currently being processed at OVHcloud
- Access to the [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/asia/&ovhSubsidiary=asia)

## Instructions

### Step 1: Create the DNS zone via the OVHcloud Control Panel

Log in to the [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/asia/&ovhSubsidiary=asia){.external}. click `Web Cloud`{.action}, then click `Order`{.action}, then `DNS zone`{.action}.

In the page that pops up, enter the domain name you would like to create an OVHcloud DNS zone for. Then wait a few moments for the tool to carry out its verifications on the domain name.

If a message appears notifying you that the DNS zone cannot be created, check that the domain name follows the requirements listed above, or ask the person managing it to do this for you. Once you have ensured that the domain name meets all requirements and is correctly configured, try again.

![dnszonecreate](images/dns-zone-create-step1.png){.thumbnail}

Once the verifications are complete, you must choose whether to enable the minimal records for the DNS zone you are going to create. The way you set your DNS records is not permanent. You can change the records after you have created the DNS zone. 

|Enable minimal records?|Details|
|---|---|
|Yes|Select this option if you would like to customise the DNS zone yourself at a later stage.|
|No|Select this option if you are planning to use OVHcloud services like a [Web Hosting plan](https://www.ovhcloud.com/asia/web-hosting/){.external}, since the zone has already been pre-configured.|

![dnszonecreate](images/dns-zone-create-step2.png){.thumbnail}

Once you have selected an option, continue following the next steps until you have created the DNS zone.

### Step 2: Edit the DNS zone (optional)

Now that your domain name’s DNS zone has been created, you can edit it. This step is optional, but it may be essential if you want to ensure that any services linked to your domain name do not experience any downtime (e.g. your website and email services).

If you would like to edit this DNS zone, click `Web Cloud`{.action} in the [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/asia/&ovhSubsidiary=asia), then click `Domain names`{.action} and choose the domain name concerned. Go to the `DNS zone`{.action} tab.

> [!primary]
>
> If you have just created the DNS zone but the domain name does not appear under the list of services in the `Domain names`{.action} section, please wait a few moments, then reload the page.
>

Once it appears, make the required changes. To learn more about how to edit a DNS zone, please read our guide to [Editing an OVHcloud DNS zone](/pages/web/domains/dns_zone_edit){.external}. Once you have modified your domain name’s OVHcloud DNS zone, you will need to allow 4-24 hours for the changes to fully propagate and take effect.

### Step 3: Edit the DNS servers for a domain name

Once the OVHcloud DNS zone is ready to be used, you can then link it to your domain name. To do this, you will need to retrieve the details for the OVHcloud DNS servers activated for your domain name in the OVHcloud Control Panel. The servers will appear below `Name Servers`{.action}.

![dnszonecreate](images/dns-zone-create-step3.png){.thumbnail}

Once you have the details, **edit your domain name’s DNS servers using the interface supplied by your domain name’s service provider**. Once you have modified the DNS zone configuration, you will need to allow 48 hours for the changes to fully propagate.

## Go further

[Editing an OVHcloud DNS zone](/pages/web/domains/dns_zone_edit)

Join our community of users on <https://community.ovh.com/en/>.
