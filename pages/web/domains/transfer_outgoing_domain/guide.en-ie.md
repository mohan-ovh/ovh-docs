---
title: Transferring a domain name to another registrar
slug: outgoing-transfer-of-generic-or-geographical-domain-name
excerpt: Find out how to move a domain name from OVHcloud to a provider of your choice
section: Transfer
order: 4
---

**Last updated 25th January 2021**

## Objective

**Domain transfer** refers to the process of moving a registered domain name from one registrar to another. For example, if you have ordered a domain name on our website, OVHcloud is its current registrar. An outgoing domain transfer needs to be initiated by the new registrar. 

In order to prevent unauthorised domain transfers, domain names are usually locked by having the status *clientTransferProhibited* set. This protection must be lifted in the OVHcloud Control Panel before starting a transfer.

**This guide explains how to prepare your domain name for an outgoing transfer.**

## Requirements

- a [domain name](https://www.ovh.ie/domains/) registered with OVHcloud
- access to the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.ie/&ovhSubsidiary=ie) with the necessary permissions to manage the domain name (domain administrator)
- the registration of the domain name in question was at least 60 days ago **and** it has not been transferred or traded (i.e. change of owner) during the last 60 days

> [!primary]
>
> If you are the domain's **owner** but you are currently not able to manage it in the OVHcloud Control Panel, neither by using your own access nor via your domain's administrative contact, please consult [this guide](../../customer/managing-contacts/#special-case-of-a-domain-owner) first before proceeding.
>

## Instructions

> [!warning]
>
> The following instructions describe the most common way to transfer a domain name, valid for most Top Level Domains (TLD). However, the specific rules for processes regarding TLDs are solely defined by the appropriate allocation authority i.e. the **registry**. Registrars such as OVHcloud must adhere to these rules and have no influence over registry decisions.
>
> The exact procedure for domain transfers may therefore vary, especially in case of some country-code TLDs (ccTLD, such as .lu, .uk, .hk, .ro) and a few special purpose TLDs (.am, .fm, etc.). Transfers might also be prohibited for various reasons, e.g. outstanding payment, abuse case or registry lock. 
>
> We recommend to consult the following resources in case of any doubt:
>
> - the website of the respective TLD registry
> - the [list of TLDs available at OVHcloud](https://www.ovh.ie/domains/prices/)
> - [ICANN's explanation of EPP Status Codes](https://www.icann.org/resources/pages/epp-status-codes-2014-06-16-en) (to find out which status codes currently apply to your domain name, carry out a *Whois* search, preferably using the respective TLD registry's website)
> - your new registrar's website and management interface, especially for questions about a pending transfer process
>

### Step 1: Remove the transfer protection for the domain name

Log in to your [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.ie/&ovhSubsidiary=ie) and select `Web Cloud`{.action} in the top navigation bar. Click `Domain names`{.action} in the services bar on the left-hand side, then choose the domain name concerned.

On the `General information`{.action} tab you can find the "Protection against domain name transfer" slider button under **Security**, set to `Enabled`{.action} by default.

![outgoingtransfer](images/outgoing-transfer-step1.png){.thumbnail}

Click on the slider and confirm in the popup window that you want to remove this protection. Allow a few minutes for the status to change to `Disabled`{.action}.

![outgoingtransfer](images/outgoing-transfer-step2.png){.thumbnail}

You can also refresh the page if it seems to take longer.

> [!primary]
>
> Once the status has changed, the domain name will remain unlocked for seven days. After this period, the protection will automatically turn back on. If you do not request a domain transfer at your new registrar during this time, it will be necessary to unlock the domain again.
>

### Step 2: Retrieve the transfer code

Once the status is set to `Disabled`{.action}, a link labelled `AUTH/INFO`{.action} will appear. Clicking on this link will open a window that contains your AUTH/INFO code (also known as transfer key, domain password, AUTH-CODE or EPP-Code).

![outgoingtransfer](images/outgoing-transfer-step3.png){.thumbnail}

The code will be requested by your new registrar to complete the transfer process. You can verify the details with your provider.

Make sure to copy and paste the code as opposed to typing it by hand, since some characters are easily confused.

### Step 3: Launch the transfer at your new registrar

After completing the previous steps you can initiate the transfer, usually by placing an order. Afterwards, the transfer may take up to 10 days. 

You can contact your provider for more information about this process.

## Go further

[Transferring a .uk domain name to another registrar](../outgoing_couk_domain_name_transfer/)

Join our community of users on <https://community.ovh.com/en/>.