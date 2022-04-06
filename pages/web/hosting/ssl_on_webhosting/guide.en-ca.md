---
title: 'Managing SSL certificates on a Web Hosting plan'
slug: ssl-certificates-on-web-hosting-plans
excerpt: 'Find out how to configure your SSL certificate on an OVHcloud Web Hosting plan'
section: 'SSL'
order: 1
---

**Last updated 4th March 2021**

## Objective

You can manage an SSL certificate on your Web Hosting plan. You can either order a certificate through OVHcloud, or you can order one elsewhere and import it on to your Web Hosting plan. Once you have set it up, it will provide one or more of your websites with a secure SSL connection, enabling the websites to work in HTTPS. 

**Find out how to manage an SSL certificate on an OVHcloud Web Hosting plan.**

## Requirements

- an [OVHcloud Web Hosting plan](https://www.ovhcloud.com/en-ca/web-hosting/){.external}
- at least one [domain name](https://www.ovhcloud.com/en-ca/domains/){.external}
- access to the [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/en/&ovhSubsidiary=ca)

## Instructions

The guide sections below describe the options available when managing an SSL certificate on your OVHcloud Web Hosting plan. Follow the instructions according to the actions you need to carry out.

- [Enabling SSL on a multisite](#multisite): You can give several of your multisites a secure SSL connection, depending on the Web Hosting plan and the certificate type.
- [Enabling SSL on your Web Hosting plan](#enablessl): Helps you activate an SSL certificate on your Web Hosting plan. This can be a free or paid certificate ordered from OVHcloud, or you can import your own SSL certificate ordered from another provider.
- [Regenerating SSL certificates on a Web Hosting plan](#regeneratessl): Helps you regenerate an SSL certificate on your Web Hosting plan when you activate SSL on one or more multisites. 
- [Deleting SSL certificates on a Web Hosting plan](#deletessl): Helps you delete an SSL certificate on an OVHcloud Web Hosting plan. Please note that this may pose a risk, if any of your websites are currently using the certificate you intend to delete. 

### Enabling SSL on a multisite <a name="multisite"></a>

Depending on which [SSL certificate](https://www.ovhcloud.com/en-ca/web-hosting/options/ssl/){.external} you would like to order, you can activate a secure SSL connection on one or more of your multisites. To do this, log in to the [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/en/&ovhSubsidiary=ca) and switch to `Web Cloud`{.action}. Click `Hosting Plans`{.action} and select the plan concerned. Click on the `Multisite`{.action} tab.

The table displayed will contain all of the domain names that have been added to your Web Hosting plan. In the "SSL" column, you will see the activation status for secure SSL connections on your multisites. 

![managessl](images/manage-ssl-step5.png){.thumbnail}

There are three status types that may appear:

|Status|Description|
|---|---|
|Enabled|An SSL certificate has already been activated for this multisite. However, if your website is not available via HTTPS, please refer to the instructions listed in our guide on [Activating HTTPS on your website with an SSL certificate](../activate-https-website-ssl/).|
|To generate|An SSL certificate has been activated for this website, but it is still not technically active. To activate the SSL certificate properly, you will need to [regenerate the certificate](#regeneratessl), in order to include the new domain names.|
|Disabled|An SSL certificate has not been activated for this multisite. To activate it, follow the steps listed below.|

To activate SSL on a multisite, click on `...`{.action} icon to the right of the multisite concerned, then `Modify domain`{.action}. In the window that pops up, tick the `SSL`{.action} box. You can also tick the option to modify the www subdomain at once if you modify its proper domain name. Then follow the steps until you confirm the change.

![managessl](images/manage-ssl-step6.png){.thumbnail}

Once you have submitted the activation request, the SSL secure connection status for the mutisite concerned should refresh in a few seconds, with the status changed to "To generate". Repeat this action as necessary if you would like to activate SSL for other multisites. 

> [!primary]
>
> You can have two situations in this state:
>
> - **You do not have a certificate.**  
>     Go to the section [Enabling SSL on a multisite](#enablessl) and choose "Free certificate (Let's Encrypt)" which supports multisites.
>
> - **SSL certificate is active, but have you added more multisites.**  
>     Proceed to [Regenerating SSL certificates on a Web Hosting plan](#regeneratessl) to regenerate the SSL certificate for the remaining multisites.
>

### Enabling SSL on your Web Hosting plan <a name="enablessl"></a>

With an OVHcloud Web Hosting plan, you can choose from a range of [SSL certificate solutions](https://www.ovhcloud.com/en-ca/web-hosting/options/ssl/){.external}:

- a free Let's Encrypt SSL certificate ([included with compatible Web Hosting plans](https://www.ovhcloud.com/en-ca/web-hosting/options/ssl/){.external})
- a paid SSL certificate ([available as an option with compatible Web Hosting plans](https://www.ovhcloud.com/en-ca/web-hosting/options/ssl/){.external})
- importing an SSL certificate ordered from another provider

To start activating your certificate, log in to the [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/en/&ovhSubsidiary=ca) and switch to `Web Cloud`{.action}. Click `Hosting Plans`{.action} and select the plan concerned. Click on the `General information`{.action} tab. Beneath "SSL certificate", the word "No" should be visible, showing that no SSL certificates have been set up on your Web Hosting plan.

> [!primary]
>
> Before you configure this, make sure that the previous step of [Activating an SSL certificate on a multisite](#multisite) was done correctly - at least one domain must have the SSL option `Enabled` or in the status `To generate` to successfully activate the Let's Encrypt SSL certificate.<br>
> This information does not apply if you select `Paid certificate`{.action} or `Import your own certificate`{.action}. 
>

Click on `...`{.action} next to "SSL certificate", then `Order an SSL certificate`{.action}.

If the word "Yes" is visible, an SSL certificate has already been set up on the Web Hosting plan. As a result, you will not be able to order another certificate while the existing one is active.

![managessl](images/manage-ssl-step1.png){.thumbnail}

In the window that appears, select the SSL certificate you would like to order. Depending on the [Web Hosting plan](https://www.ovhcloud.com/en-ca/web-hosting/){.external} you have ordered and its configuration, it may be the case that none of the solutions listed below are available. Once you have selected an option, click on the `Next`{.action} button.

![managessl](images/manage-ssl-step2.png){.thumbnail}

Depending on which solution you have selected, there may be additional steps.

- **If you have selected a free SSL certificate:** You will not need to take any further actions, unless there is a technical element stopping the SSL certificate from being activated (a message will then appear in the OVHcloud Control Panel listing the elements you need to check) or a domain name validation for SSL certificate delivery. In this case, you would be notified in advance, and should follow the instructions sent to you.

- **If you have selected a paid SSL certificate:** You will need to complete the order process in order to receive a certificate. Special validation may be required for certain SSL certificate types. You may receive one or more emails regarding this validation. If this is the case, please read the information included in these emails and follow any instructions provided in order to complete the setup.

- **If you have chosen to import an SSL certificate:** You will need to enter the certificate details into the boxes that appear. Please refer to the information sent by the service provider you ordered the certificate from. 

Certificate setup may take between several minutes and several days, depending on the type of certificate you have chosen. To check if the SSL certificate has been set up on your Web Hosting plan, go to the `General information`{.action} tab in the OVHcloud Control Panel. The word "Yes" should then appear below "SSL certificate". 

![managessl](images/manage-ssl-step4.png){.thumbnail}

### Regenerating SSL certificates on a Web Hosting plan <a name="regeneratessl"></a>

> [!primary]
>
> This operation only applies to certificates that can activate a secure SSL connection for several multisites.
>

Once you have activated a secure SSL connection across one or more of your multisites, the status will then change to `To generate`. This generation is essential for adding the domain names concerned to the SSL certificate on your Web Hosting plan. 

To do this, log in to the [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/en/&ovhSubsidiary=ca) and switch to `Web Cloud`{.action}. Click `Hosting Plans`{.action} and select the plan concerned. Click on the `General information`{.action} tab. Then click on `...`{.action} next to "SSL certificate", then `Regenerate SSL certificate`{.action}.


![managessl](images/manage-ssl-step7.png){.thumbnail}

Read the information listed in the window that appears, then click `Confirm`{.action}. Then wait for your SSL certificate to be regenerated. This may take several hours.

Please note that Let's Encrypt, the authority that delivers the SSL certificate offered free with your Web Hosting plan, has a [limit of five regenerations per week](https://letsencrypt.org/docs/rate-limits/){.external}. As a result, we advise taking care with regenerations over a short-term period, so you can avoid being temporarily blocked.

![managessl](images/manage-ssl-step8.png){.thumbnail}

### Deleting SSL certificates on a Web Hosting plan <a name="deletessl"></a>

You can also delete an SSL certificate that has been set up on your Web Hosting plan. Before you start making any changes, **we strongly advise ensuring that the certificate deletion will not render your websites inaccessible**. Please keep in mind that your web users will see a security error when they try to access a website that works in HTTPS, but does not have a secure SSL connection. 

Since this verification involves checking your website settings, we recommend contacting a specialist service provider if you experience any difficulties in this regard. We will not be able to assist you with this ourselves. 

Once you are ready to delete the SSL certificate, log in to the [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/en/&ovhSubsidiary=ca) and switch to `Web Cloud`{.action}. Click `Hosting Plans`{.action} and select the plan concerned. Click on the `General information`{.action} tab. Then click on `...`{.action} next to "SSL certificate", then `Delete SSL`{.action}.

On the page that appears, confirm the deletion. The deletion will take effect within a few hours. 

![managessl](images/manage-ssl-step9.png){.thumbnail}

## Go further

Join our community of users on <https://community.ovh.com/en/>.
