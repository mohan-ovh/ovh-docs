---
title: 'Configuring your Email Pro solution'
slug: first-configuration-email-pro
excerpt: 'Find out how to configure your Email Pro solution'
section: General
---

**Last updated 9th April 2020**

## Objective

You have just purchased an Email Pro solution, which gives you affordable professional email addresses to support or start up your business.

**This guide explains the steps to correctly configure your Email Pro solution.**

## Requirements

- an [Email Pro](https://www.ovh.ie/emails/email-pro/) solution
- an email confirming that your Email Pro solution has been set up
- a domain name
- access to the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager)

## Instructions

### Step 1: Log in to your service’s interface

Once the Email Pro service has been created and is available, you can manage it from the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager).

To do this, log in, then click on `Email Pro`{.action} in the services menu on the left and select the appropriate service.

> [!primary]
>
> The name of an Email Pro service in the OVHcloud Control Panel begins with *emailpro-*, contains part of your NIC handle, and ends with a figure (1 for the first Email Pro service installed, 2 for the second, etc.).
>

### Step 2: Add your domain name

If you have just ordered your Email Pro service, a window will automatically pop up, prompting you to `Add a domain`{.action}. If the window does not pop up, go to the `Associated domains`{.action} tab, then click on the `Add a domain`{.action} button.

You will need to choose from:

- **Choose a domain from the list.** Only the domains that use the OVHcloud configuration and are connected to your NIC handle will appear.
- **Enter a domain name which is not managed by your OVHcloud account.** You should be able to modify the domain name’s configuration (its DNS zone) so that the Email Pro service can function correctly.

Once you have selected an option, click on the `Next`{.action} button.

![emailpro](images/first_config_email_pro_add_domain.png){.thumbnail}

The window will then appear, showing information on configuring a mode.

- **If you have entered a non-OVHcloud domain name**: nonauthoritative mode will be configured by default.
- **If you have selected an OVHcloud domain name in the list**: you must choose between two modes.

|Mode|Description|
|---|---|
|Authoritative|Choose this if you only use the Email Pro solution with your domain name. In authoritative mode, you cannot use another email solution with your Email Pro service.|
|Nonauthoritative|Choose this if you use your Email Pro solution domain name with another email solution.| 

> [!primary]
>
> The mode choice is not definitive. It can be modified via the OVHcloud Control Panel later on.
>

Click on the `Next`{.action} button to continue adding the domain.

![emailpro](images/first_config_email_pro_add_domain_step2.png){.thumbnail}

**If you have selected an OVHcloud domain name in the list**, it will be automatically configured. To do this, tick the boxes and click on the `Next`{.action} button to continue adding the domain.

![emailpro](images/first_config_email_pro_add_domain_step3.png){.thumbnail}

- **SRV**: DNS records defining specific information used to identify the values necessary to connect to a service; in this case they enable an email client software to be automatically configured for your email account ("Autodiscover").
- **MX**: DNS records pointing a domain name to an email server and therefore necessary for the reception of emails.

**For a non-OVHcloud domain name**, continue with step 3.

At the end of the configuration process, please check the information you have entered, then click on the `Confirm`{.action} button to add the domain.

### Step 3: Configure your domain name

Once you have added the domain name as an associated domain, you can check its configuration using the table on the `Associated domains`{.action} tab.

You can use the `Diagnosis`{.action} column to modify the domain name’s DNS configuration. A red box will appear if these configurations need to be changed. There are two options:

- **Automatic configuration, when adding an OVHcloud domain name:** it may take a few hours after the modification before it is correctly displayed in the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager).

- **Manual configuration, when adding a non-OVHcloud domain name:** click on the red box to verify the changes you need to make. <br>_For a CNAME record_, please refer to our guide on [Creating a CNAME record to add an associated domain](https://docs.ovh.com/ie/en/microsoft-collaborative-solutions/exchange_20132016_how_to_add_a_cname_record/). <br>_For an MX record_, please refer to our guide [Add an MX record to your domain name’s configuration](https://docs.ovh.com/ie/en/domains/web_hosting_configuring_mx_with_the_ovh_dns_zone/). <br>_For an SRV record_, you can edit your DNS zone using the information provided when you click on the red "SRV" box. We recommend to consult [our guide](https://docs.ovh.com/ie/en/domains/web_hosting_how_to_edit_my_dns_zone) regarding these modifications. If you have just made the changes, they may take a few hours to be correctly displayed in the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager).

![emailpro](images/first_config_email_pro_configure_domain_update.png){.thumbnail}

### Step 4: Configure the Email Pro accounts

To configure your email addresses, go to the `Email accounts`{.action} tab. The table displays the accounts that you have ordered in this format: “*@configureme.me*”.

To configure them, click on the pencil icon.

![emailpro](images/first_config_email_pro_configure_email_accounts.png){.thumbnail}

Enter the information requested.

|Title|Description|
|---|---|
|Email account|Enter the name for your email address (firstname.lastname, for example) and select the appropriate domain in the list.|
|First name|Enter a first name.|
|Last name|Enter a last name.|
|Display name|Enter the sender name that you wish to be displayed when sending emails from this address.|
|Password confirmation|Type in a password, and confirm it.| 

Once the information is complete, click on the `Next`{.action} button, check the information displayed, then click `Confirm`{.action} to start configuring the account.

> [!primary]
>
> Repeat this step as necessary according to the number of accounts you have. You can order additional accounts using the `Order accounts`{.action} button.
>

![emailpro](images/first_config_email_pro_configure_email_accounts_step2.png){.thumbnail}

### Step 5: Use your email addresses

Once you have configured your accounts, you can start using them straight away. To do this, OVHcloud offers an online application (a *web app*), available [here](https://www.ovh.ie/mail/), and you will need to enter your email credentials.

If you would like to configure your email address on an email client or device (e.g. a smartphone or tablet), you can refer to our [configuration guides](https://docs.ovh.com/ie/en/emails-pro/). If you simply need the information required to configure your Email Pro account, the settings to use are listed below:

|Server type|Server name|Security type|Port|
|---|---|---|---|
|Incoming|pro**X**.mail.ovh.net|SSL/TLS|993|
|Outgoing|pro**X**.mail.ovh.net|STARTTLS|587|

> [!primary]
>
> In our guides, we use as the server name: pro**X**.mail.ovh.net. You will need to replace the "X" with the actual number indicating the appropriate server for your Email Pro service.
> 
> You can find this information in the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager), in the `Web`{.action} section, if you select `Professional Email`{.action} in the left-hand column. The server name is displayed in the **Connection** box in the `General Information`{.action} tab.
>

## Go further

Join our community of users on <https://community.ovh.com/en/>.