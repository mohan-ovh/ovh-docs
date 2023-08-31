---
title: 'Enabling and managing your OVHcloud SharePoint'
excerpt: 'Find out how to order and configure a SharePoint platform'
updated: 2023-06-19
---

## Objective

The SharePoint offers allow you to benefit from a storage space of 1 TB shared with the other accounts of your SharePoint platform, for your collaborative work.

You also have 100 GB of personal storage space for each account on your SharePoint platform.

**This guide explains how to order and configure a SharePoint platform.**

## Requirements

- access to the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.ie/&ovhSubsidiary=ie)
- an [OVHcloud Exchange solution](https://www.ovhcloud.com/en-ie/emails/hosted-exchange/) already set up (for enabling an associated SharePoint platform)

## Instructions

### Step 1: Order a SharePoint platform

Log in to your [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.ie/&ovhSubsidiary=ie) and go to the `Webcloud`{.action} section to begin ordering your SharePoint platform.

There are two platform types available:

| Associated SharePoint                                                                                                                      	| Standalone SharePoint                                                                                                                                                                       	|
|-----------------------------------------------------------------------------------------------------------------------------------------	|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| ![sharepoint](images/order-manage-sharepoint-02.png){.thumbnail}                                                                        	| ![sharepoint](images/order-manage-sharepoint-03.png){.thumbnail}                                                                                                                            	|
| If you have a Hosted Exchange platform in your OVHcloud account, you can link the accounts to a SharePoint platform. Select the account(s) to which you wish to link a SharePoint licence. 	| If you do not have an OVHcloud Hosted Exchange platform or you wish to have a standalone SharePoint platform, select ‘Order a SharePoint Standalone account’. <br>Set the number of licences that you wish to have according to the number of users.	|

Once you have chosen, click on `Order your solution`{.action} to complete your order.

### Step 2: Activate the SharePoint platform

Once your order has been confirmed and paid for, a confirmation email will be sent to the email address registered in your OVHcloud account, indicating that the platform is ready to be configured.

To read this email, log in to your [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.ie/&ovhSubsidiary=ie), click on your account name in the top right-hand corner, then click on `Service emails`{.action}. Search for an email with the subject:

> **\[xx-11111-ovh] Configure your Microsoft SharePoint service!**

To start the configuration, go to the `Web Cloud` section of your Control Panel. Click on `Microsoft`{.action}, then on `SharePoint`{.action}. Then, select the appropriate SharePoint platform.

Enter the name of your platform in the “SharePoint URL” box, then click `Confirm URL`{.action}.

![sharepoint](images/order-manage-sharepoint-04.png){.thumbnail}  

> [!warning]
>
> Once confirmed, the SharePoint’s name cannot be modified.

### Step 3: Configure the SharePoint platform

Log in to your [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.ie/&ovhSubsidiary=ie) and select `Web Cloud`{.action} in the top navigation bar. Click `Microsoft`{.action}, then `SharePoint`{.action}. Next, select the SharePoint service concerned.

#### **Standalone SharePoint**

As this platform is standalone, you need to link a domain name before configuring your users.

##### ***Add a domain***

Click on the `Domains` tab and then on `Add a domain`{.action}. Click on a domain from your account or select an external domain name that you manage. 

- If you select a domain name available in your Control Panel, it will be automatically validated, and you only need to configure your users.
 
- If you select an external domain name, you need to add a CNAME record to the domain name’s DNS zone in order to validate it on SharePoint. The CNAME record to enter can be accessed by clicking on the information icon next to ‘Validating domain’, as shown below.

![sharepoint](images/order-manage-sharepoint-05.png){.thumbnail}

##### ***Configure a user***

Click on the `Users` tab, then on `...`{.action} to the right of the account, then click on `Modify the account`{.action}.

![sharepoint](images/order-manage-sharepoint-06.png){.thumbnail} 

Enter the user information into the popup window, and click on `Confirm`{.action}.

To obtain administrator rights on SharePoint, click on `...`{.action} again to the right of the account, then click on `Enable administrator rights`{.action}.

#### **Associated SharePoint**

As the name suggests, this platform is linked to the Exchange platform that you selected when ordering, so there is no domain name to link.

##### ***Configure a user***

Click on the `Users` tab on your platform to view all of the Exchange accounts that can be used with a SharePoint licence.

![sharepoint](images/order-manage-sharepoint-07.png){.thumbnail} 

The `Active account` column indicates whether the Exchange account can use a SharePoint licence. 

> [!primary]
>
> If you wish to activate a licence on an account that does not have one, click on `...`{.action} to the right of the account, then click on `Enable SharePoint`{.action}.

By default, an account with a licence does not have administrator rights. To enable them, Click on `...`{.action} to the right of the account, then on `Enable administrator rights`{.action}.

![sharepoint](images/order-manage-sharepoint-08.png){.thumbnail} 

#### **Restore administrator rights**

On both types of SharePoint service, there is a `Restore administrator rights`{.action} button in the `Users` tab. This allows you to re-establish a user’s administrator rights on the platform if they have been wrongly configured in the SharePoint interface.

![sharepoint](images/order-manage-sharepoint-09.png){.thumbnail}

## Go further

Join our community of users on <https://community.ovh.com/en/>.
