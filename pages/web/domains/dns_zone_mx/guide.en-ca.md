---
title: "Add an MX record to your domain name’s configuration"
excerpt: "Find out how to add a MX record to your OVHcloud domain name’s configuration"
updated: 2018-05-30
---

**Last updated 21th September 2022**

## Objective

An MX record is used to point a domain name to an email server. It enables servers sending emails to your email addresses to know where they must transfer them to. Your service provider is likely to have several email servers. Because of this, you will need to create several MX records.

**Find out how to add a MX record to your OVHcloud domain name’s configuration.**

## Requirements

- You must have permission to manage the domain name from your [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/en/&ovhSubsidiary=ca){.external}.
- You must be logged in to your [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/en/&ovhSubsidiary=ca){.external}.
- The domain name must use the OVHcloud configuration (i.e. the OVHcloud DNS servers).

> [!warning]
>
> - If your domain name does not use the OVHcloud DNS servers, you will need to modify the MX records using the interface given by the provider that manages your domain name configuration.
>
> - If your domain name is registered with OVHcloud, you can check if it is using the OVHcloud configuration in your [Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/en/&ovhSubsidiary=ca){.external}. Select the domain, and go to the `DNS servers`{.action} tab.
>

## Instructions

### Step 1: Understand the basic purpose of MX records

An MX record links your domain name to your email service provider’s servers (e.g. OVHcloud’s servers). When you are sent an email, the server sending the email will use the MX record to find out which server it should deliver to.

You can add multiple MX records to a single domain name, so you will need to define a priority for each record. By doing so, the servers sending emails to your email address will know which server they should deliver them to, by priority. However, please note that when you add multiple MX records, the servers they point to must belong to the same service provider.

Generally speaking, **changing MX records is a tricky task**. If you make any mistakes configuring MX records, your email addresses may be unable to receive new emails as a result. For this reason, we strongly advise that you take great care when carrying out these configuration changes.

### Step 2: Familiarise yourself with the OVHcloud MX configuration

In the table below, we have listed the OVHcloud MX configuration to use for our MX Plan solutions (both as a standalone solution, or included as part of our [OVHcloud Web Hosting plans](https://www.ovhcloud.com/en-ca/web-hosting/){.external}, and [Exchange](https://www.ovhcloud.com/en-ca/emails/hosted-exchange/){.external} solutions. Our email servers also have anti-spam and anti-virus protection.

|Domain|TTL|Record type|Priority|Target|
|---|---|---|---|---|
|*leave blank*|3600|MX|1|mx0.mail.ovh.ca.|
|*leave blank*|3600|MX|5|mx1.mail.ovh.ca.|
|*leave blank*|3600|MX|50|mx2.mail.ovh.ca.|
|*leave blank*|3600|MX|100|mx3.mail.ovh.ca.|
|*leave blank*|3600|MX|200|mx4.mail.ovh.ca.|

You will now need to add these MX records to your domain name’s DNS zone configuration. The next step will help you do so, in your domain name’s OVHcloud DNS zone.

### Step 3: Modify an OVHcloud MX record’s configuration

To modify the MX records in your domain’s OVHcloud configuration, log in to your [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/en/&ovhSubsidiary=ca){.external}. Select `Domains`{.action}, click on the domain, then go to the `DNS Zone`{.action} tab.

This table displays your domain’s OVHcloud configuration. Each row corresponds to a DNS record. To start with, please check if the MX records already exist in your domain name’s OVHcloud DNS zone configuration. You can do this using the search filter.

![dnsmxrecord](images/mx-records-dns-zone.png){.thumbnail}

If there are already MX records and you would like to replace them, click on the `...`{.action} icon on the right-hand side of each table row, then click `Delete record`{.action}. Please ensure, however, that you don’t delete all MX records before you add the new ones.

To check if MX records already exist, use the filter above the DNS table to select the **MX** field, then confirm to only display the MX DNS records for your DNS zone.

To add a record, click `Add record`{.action} button to the right of the table, then select `MX`{.action}. Fill in the information required, depending on the email solution you have ordered:

- **If you have an OVHcloud email solution:** Please refer to the information provided in [Step 2: Familiarise yourself with the OVHcloud MX configuration](/pages/web/domains/dns_zone_mx#step-2-familiarise-yourself-with-the-ovh-mx-configuration).

- **If you are using an email solution from another service provider:** Please refer to the information given by your service provider.

Once you have entered the information, finalise the steps, then click `Confirm`{.action}.

> [!primary]
>
> The change can take 4-24 hours to fully propagate.
>

## Go further

[General information about DNS servers](/pages/web/domains/dns_server_general_information){.external}

[Web hosting: How to edit your DNS zone](/pages/web/domains/dns_zone_edit){.external}.

For specialised services (SEO, development, etc.), contact [OVHcloud partners](https://partner.ovhcloud.com/en-ca/).

If you would like assistance using and configuring your OVHcloud solutions, please refer to our [support offers](https://www.ovhcloud.com/en-ca/support-levels/).

Join our community of users on <https://community.ovh.com/en/>.
