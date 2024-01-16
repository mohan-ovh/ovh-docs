---
title: 'Creating an email address with an MX Plan solution'
excerpt: 'Find out how to create an email address with an MX Plan solution'
updated: 2022-10-11
---

## Objective

You have just purchased an MX Plan email solution. It allows you to benefit from email addresses associated with a domain name.

**Find out how to create an email address with an MX Plan solution.**

## Requirements

- An MX Plan solution, available as part of our [Web Hosting plans](https://www.ovhcloud.com/en-sg/web-hosting/)
- Access to the [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/sg/en/&ovhSubsidiary=ca){.external}, in the `Web Cloud`{.action} section

## Instructions <a name="instructions"></a>

To do this, log in to the [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/sg/en/&ovhSubsidiary=ca){.external}, and open the `Web Cloud`{.action} section. Click on `Emails`{.action}.

### Access the email service management

If you are using the new version of the MX Plan solution, your display should correspond to the following image. If this section looks different for you, please double-check that you are following the right set of instructions [by referring to the information above](./#instructions).  

![email](images/mxplan-creation-new-step1.png){.thumbnail}

### Create an email account

To set up a new email account, go to the `Email accounts`{.action} tab. The window that opens will display the email accounts that are already available, as well as those you can still create. Next, click the `Add Account`{.action} button.

![email](images/mxplan-creation-new-step2.png){.thumbnail}

In the popup window, enter the following information:

- **Email account**: A temporary name is already prefilled in the text box. Replace it with the name you would like for your email address (firstname.lastname, for example). The domain name for the email address is already pre-selected in the list.
- **First name**: Enter a first name.
- **Name**: Enter a surname.
- **Name to display**: Enter the name you want to be displayed as a sender when you send emails from this address.
- **Password**: Type in a password and confirm it. For security reasons, we recommend not using the same password twice and choosing one that does not contain any personal information (e.g. your surname, first name and date of birth). We also recommend renewing it regularly.

Once you have filled in all of the required fields, click `Next`{.action}.

![email](images/mxplan-creation-new-step3.png){.thumbnail}

Next, check that all the information displayed in the summary is correct. If it is, click `Confirm`{.action}. The account you have just added will now appear in the table. You will need to wait a few minutes for the account to become available.

Repeat this step as necessary according to the number of accounts to create.

### View emails

On the [Webmail login page](https://www.ovhcloud.com/en-sg/mail/){.external}, enter your email address and password. Then click the `Login`{.action} button.

When you first log in to the webmail interface, you are prompted to set the interface language and your time zone. Your inbox will then appear. To find out how to use your email address via Outlook Web Access (OWA) webmail, use our guide ["Using the Outlook Web Access with an email account"](/pages/web_cloud/email_and_collaborative_solutions/using_the_outlook_web_app_webmail/email_owa){.external}.

![email](images/mxplan-creation-new-step5.png){.thumbnail}

To view your emails using an email client, please refer to the section ["View an email account from a device"](#configdevices).

### Delete an email account

With a new MXplan service, deleting an account is referred to as *resetting an account*.

> [!warning]
>
> Before deleting email accounts, make sure they are not used. You may need to back up these accounts. If required, please refer to our guide on [Migrating your email address manually](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration), which explains how to export account data from your Control Panel or email software.

In the `Email accounts`{.action} tab, click the `...`{.action} button to the right of the account you want to delete, then click `Reset this account`{.action}.

![email](images/mxplan-new-reset.png){.thumbnail}

### View an email account from a device <a name="configdevices"></a>

You will need to configure your email address on the device you want to use (e.g. a smartphone or tablet). To do this, you can use our configuration guides:

> [!tabs]
> **Windows**
>>
>> - [Mail on Windows 10](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/how_to_configure_windows_10)
>> - [Outlook](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/how_to_configure_outlook_2016)
>> - [Thunderbird](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/how_to_configure_thunderbird_windows)
>>
> **Apple**
>>
>> - [macOS email](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/how_to_configure_mail_macos)
>> - [Mail for iPhone or iPad](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/how_to_configure_ios)
>> - [Outlook Mac OS](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/how_to_configure_outlook_2016_mac)
>> - [Thunderbird](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/how_to_configure_thunderbird_mac)
>>
> **Android**
>>
>> - [Android](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/how_to_configure_android)
>>
> **Other**
>>
>> - [Gmail interface](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/how_to_configure_gmail)
>>

If you just need the information required to configure your email address, the settings to use are listed below:

> [!tabs]
> **For IMAP configuration (recommended)**
>>
>> |Server type|Server name|Port (with SSL)|Port (without SSL)|
>> |---|---|---|---|
>> |Incoming|imap.mail.ovh.ca|993|143|
>> |Outgoing|smtp.mail.ovh.ca|465|587|
>>
> **For POP configuration**
>>
>> |Server type|Server name|Port (with SSL)|Port (without SSL)|
>> |---|---|---|---|
>> |Incoming|pop.mail.ovh.ca|995|110|
>> |Outgoing|smtp.mail.ovh.ca|465|587|
>>

> [!warning]
>
> If you have any problems configuring your email address on your device, we recommend using our [configuration guides](/products/web-cloud-email-collaborative-solutions-mx-plan) or contacting the publisher of the application you are using, because you may need to make a change that is specific to the application.
>

## Go further

Join our community of users on <https://community.ovh.com/en/>.