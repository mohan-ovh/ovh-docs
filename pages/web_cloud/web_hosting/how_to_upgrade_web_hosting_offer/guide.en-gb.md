---
title: Changing your web hosting plan offer
excerpt: Find out how to change the subscription offer for your OVHcloud Web Hosting plan
updated: 2023-07-16
---

## Objective

In your [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.co.uk/&ovhSubsidiary=GB), you can increase the capacity of your [web hosting offers](https://www.ovhcloud.com/en-gb/web-hosting/) to have more compute resources, storage space, databases or email accounts. Additional features such as [mailing lists](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/feature_mailing_list) (from the [Pro plan](https://www.ovhcloud.com/en-gb/web-hosting/professional-offer/)) or [Private SQL](https://www.ovhcloud.com/en-gb/web-hosting/options/private-sql/) (included with the offers of the [Performance range](https://www.ovhcloud.com/en-gb/web-hosting/performance-offer/)) will also become available with a subscription upgrade.

**Find out how to scale your OVHcloud hosting plan without any service interruptions.**

## Requirements

- An [OVHcloud web hosting plan](https://www.ovhcloud.com/en-gb/web-hosting/)
- Access to the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.co.uk/&ovhSubsidiary=GB)

## Instructions

> [!warning]
>
> **Before** you make any changes to your current subscription, check to see if you have any of these questions:
>
> - [How do I upgrade my 100M free hosting solution to a web hosting plan?](#start10m)
> - [How do I get a temporary performance boost on my Performance hosting plan?](#boost)
> - [Will I waste the time remaining on my current hosting plan when I change plans?](#billing)
> - [Can I upgrade my current plan to a lower plan?](#checks)
>

### Modifying your hosting plan <a name="modify"></a>

To change your subscription, go to your [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.co.uk/&ovhSubsidiary=GB) in the `Web Cloud`{.action} section. Click `Hosting plans`{.action} and select the plan concerned.

In the `Plan` box, click the `...`{.action} button to the right of `Solution`, then `Change plan`{.action}.

![change_plan](images/change_plan.png){.thumbnail}

Then select your new subscription and its duration. Confirm the corresponding contracts, then click `Send`{.action}.

### Checking that your hosting plan is compatible with a lower plan <a name="checks"></a>

> [!warning]
>
> You can only change your subscription to a lower range plan if it is the **immediate lower range** plan.
> For example, you cannot switch from *Performance 2* to *Pro* in a single operation.
> You will **first** need to downgrade your web hosting plan from the *Performance 2* plan to the *Performance 1* plan, **and then** to the *Pro* plan.

Before you make your switch to a lower range, check the following 6 items:

#### 1 - Start SQL databases

Before moving your hosting to a lower plan, please ensure that the new plan has enough [databases](https://www.ovhcloud.com/en-gb/web-hosting/options/start-sql/). Also make sure they are of sufficient size.

Otherwise, delete unused databases and reduce the amount of data they contain, if necessary. This quantity must not exceed the maximum size of the databases in the new solution (for any requests for assistance with the operations to be carried out, contact the [OVHcloud partners](https://partner.ovhcloud.com/en-gb/directory/)).

If you have deleted data from your databases, you can recalculate the quota from the `Databases`{.action} tab in the `Hosting plans`{.action} section of the OVHcloud Control Panel. Click on the `...`{.action} button to the right of the database concerned, then `Recalculate the quota`{.action}.

![quota](images/quota.png){.thumbnail}

#### 2 - Web Cloud Databases

If you are using the [Web Cloud Databases](/pages/web_cloud/web_cloud_databases/starting_with_clouddb#clouddb-server-activation-included-with-your-web-hosting-plan) solution included with your [Performance](https://www.ovhcloud.com/en-gb/web-hosting/performance-offer/) hosting plan, and you wish to switch your hosting plan to a [Pro](https://www.ovhcloud.com/en-gb/web-hosting/professional-offer/) solution, go to the `Hosting plans`{.action} section in your Control Panel.<br>
Click the `... `{.action} button in the `Private database`{.action} section, then `Detach`{.action}.

![Web Cloud Databases](images/clouddb.png){.thumbnail}

With this action, you can order a Web Cloud Databases solution independent of your *Performance* subscription. Your server data will be stored.

If you do not want to keep this data, you can also delete your Private SQL before going to the *Pro* offer: 

1. Back up your data by following the instructions in this [guide](/pages/web_cloud/web_cloud_databases/save-export-on-database-server).<br>
2. Delete your Web Cloud Databases server via your [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.co.uk/&ovhSubsidiary=GB). To do this, click on your name in the top right-hand corner, then `Service management`{.action}. Then click on the `...`{.action} button to the right of the row concerned, then `Delete my Private SQL hosting service`{.action}.

#### 3 - FTP space

Before switching your hosting plan to a lower plan, please ensure that the new plan includes enough [FTP storage space](/pages/web_cloud/web_hosting/ftp_connection) so that you can import files from your current hosting plan.

The quota used on your FTP hosting plan is visible in the `Hosting plans`{.action} section of the OVHcloud Control Panel. Click on the `General information`{.action} tab, and you will see the quota under `Disk space`.

![ftp](images/ftp.png){.thumbnail}

#### 4 - Email accounts

Please also check that your new solution has a sufficient number of available email accounts. Otherwise, delete the extra accounts, after you have [backed up](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration) the contents if necessary.

If you would like to keep the same number of email accounts, before moving your web hosting to a lower plan, you can also order a new **MX Plan** email solution. In the `Emails`{.action} section of the OVHcloud Control Panel, click on the solution concerned, then on the `...`{.action} button to the right of `Solution`. Next, click `Change solution`{.action}.

![mxplan](images/mxplan.png){.thumbnail}

#### 5 - Mailing lists

The [Mailing lists](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/feature_mailing_list) feature is optional on [Personal](https://www.ovhcloud.com/en-gb/web-hosting/personal-offer/) hosting plans.

To set up your hosting plan on a [Personal](https://www.ovhcloud.com/en-gb/web-hosting/personal-offer/) solution, you will need to delete the mailing lists first, or order an email solution with this feature (**MX Plan 100** or **MX Plan Full**) from your [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.co.uk/&ovhSubsidiary=GB).

In the `Emails`{.action} section of your Control Panel, select the solution concerned, then click on `...`{.action} to the right of `Solution`{.action}. Next, click `Change solution`{.action}.

#### 6 - FTP users

Before switching your hosting plan to a lower plan, ensure that the new plan has enough FTP users.

You can view the number of FTP users in your OVHcloud Control Panel. Go to the `Web Cloud`{.action} section, then select the plan concerned in the `Hosting plans`{.action} section on the left-hand side. On the page that appears, click on the `FTP-SSH`{.action} tab. In the lower part of the next page, a table lists all FTP users created for your Web Hosting plan.

To delete FTP users, click the `...`{.action} to the right of the FTP user you want to delete, then `Delete`{.action}.

![user FTP deletion](images/userFTP.png){.thumbnail}

#### Completion

Once you have checked these 7 elements, you can [change your plan](#modify).

### Special cases

#### You have a 100M free hosting solution <a name="start10m"></a>

If you change your [100M free hosting](/pages/web_cloud/web_hosting/activate_start10m) solution, you will only be offered the [Personal Hosting plan](https://www.ovhcloud.com/en-gb/web-hosting/personal-offer/). However, once you have switched to the Personal hosting plan, you can migrate it to all of our [web hosting plans](https://www.ovhcloud.com/en-gb/web-hosting/).

Please follow [these instructions](#modify) to change your plan.

#### Boost your Performance web hosting plan temporarily <a name="boost"></a>

With the [Boost option](https://www.ovhcloud.com/en-gb/web-hosting/options/boost/), available on our *Performance* plans, you can temporarily increase your hosting system’s CPU and RAM resources to absorb seasonal traffic spikes. If this increase is prolonged over time, you can also [switch to a higher-level Performance plan](#modify) to have these resources permanently.

> [!warning]
>
> When you choose to enable the Boost option, the option remains active and is billed **until you disable it**.

If the **Boost** option suits your needs, below are the instructions for **enabling** or **disabling** this option on your web hosting plan.

> [!tabs]
> **Enable the Boost option**
>>
>> In the `General information` section of your Web Hosting plan, click on the `...`{.action} button to the right of `Boost`, then `Boost my plan`{.action}.<br><br>
>> ![boost](images/enable_boost.png){.thumbnail}<br>
>>
> **Disable the Boost option**
>>
>> In the `More` tab of your web hosting plan, click `Boost my plan`{.action}.<br>
>> The Boost option usage table will appear, click `Disable boost plan`{.action}.<br><br>
>> ![boost](images/disable_boost.png){.thumbnail}<br>

#### Billing in case of a change of offer <a name="billing"></a>

When you upgrade your original plan to a higher plan, a *prorata temporis* calculation will be applied until the next renewal date for your original plan.
This calculation corresponds to the price difference between your initial solution and your new solution.

> **Example:**<br>
>
> You subscribed to a [Personal Hosting](https://www.ovhcloud.com/en-gb/web-hosting/personal-offer/) subscription on January 1, 2022.
>
> On October 31, 2022, you upgrade from this **Personal** plan to a [Pro plan](https://www.ovhcloud.com/en-gb/web-hosting/professional-offer/).<br>
>
> Therefore, the amount corresponding to the remaining duration on the **Personal** subscription (2 months, from November 1, 2022 to January 1, 2023) is automatically deducted from the cost of the new **Pro** subscription, until January 1, 2023. You will only pay the difference.
> From 1st January 2023, you will then be billed for your Pro subscription at its current price.

Please follow [these instructions](#modify) to change your plan.

## Go further <a name="gofurther"></a>

[Accessing a website’s logs and statistics on a web hosting](/pages/web_cloud/web_hosting/logs_and_statistics)

[Optimising your website’s performance](/pages/web_cloud/web_hosting/optimise_your_website_performance)

For specialised services (SEO, development, etc.), contact [OVHcloud partners](https://partner.ovhcloud.com/en-gb/directory/).

If you would like assistance using and configuring your OVHcloud solutions, please refer to our [support offers](https://www.ovhcloud.com/en-gb/support-levels/).

Join our community of users on <https://community.ovh.com/en/>.
