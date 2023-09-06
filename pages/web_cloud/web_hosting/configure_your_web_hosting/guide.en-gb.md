---
title: "Web Hosting - Environment, PHP version, ".ovhconfig""
excerpt: "Find out how to modify a web hosting plan’s runtime environment, PHP version, application firewall, engine, mode and ".ovhconfig""
updated: 2023-09-05
---

## Objective

The [OVHcloud Web Hosting](https://www.ovhcloud.com/en-gb/web-hosting/){.external} offers  allow you to host the website you want, provided that it is compatible with the [configuration of our shared infrastructure](https://webhosting-infos.hosting.ovh.net){.external}.
However, on our shared infrastructure, you can modify the following settings for your web hosting plan:

- [runtime environment](#runtime-environment)
- [PHP version](#php-versions)
- [the PHP runtime environment](#php-runtime)
- [the application firewall](#firewall)
- [the runtime mode](#runtime-mod)

These configuration settings can be modified in two ways:

- from your [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.co.uk/&ovhSubsidiary=GB);
- From the FTP storage space of your OVHcloud web hosting plan using a file named ".ovhconfig".

> [!primary]
>
> .ovhconfig files are server configuration files and are automatically recognized as such by the shared hosting infrastructure.
> They are present natively and by default in the "FTP root" of your web hosting plan’s FTP storage space.
> They contain the values of the elements mentioned above.
>

In short, changing your Web Hosting plan’s configuration from the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.co.uk/&ovhSubsidiary=GB), or changing the values in the .ovhconfig file is the same as doing the same.

### Summary

- [1 - Description of configuration settings available on OVHcloud web hosting plans](#all-parameters)
- [2 - Method 1: Modify the web hosting plan configuration via the OVHcloud Control Panel](#setting-ovh-manager)
- [3 - Method 2: Modify the web hosting plan configuration from the ".ovhconfig" file](#setting-ovhconfig)
- [4 - Advanced use of .ovhconfig files](#ovhconfig-more)

**Find out how to modify a web hosting plan’s runtime environment, PHP version, application firewall, engine, mode and .ovhconfig file.**

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/X31MNMLw064" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Requirements

- You must have a [OVHcloud web hosting plan](https://www.ovhcloud.com/en-gb/web-hosting/){.external}, with the exception of a [Cloud Web hosting plan](https://www.ovhcloud.com/en-gb/web-hosting/cloud-web-offer/).
- access to your web hosting plan from the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.co.uk/&ovhSubsidiary=GB), or information on how to log in to the [FTP storage space](/pages/web_cloud/web_hosting/ftp_connection).

## Instructions

### 1 - Description of the configuration settings available on OVHcloud web hosting plans <a name="all-parameters"></a>

Before you begin, please find the technical description below for each of the settings that you can modify on OVHcloud web hosting plans.

> [!warning]
>
> Modifying at least one of these elements may affect the display or the proper functioning of your website. **Please ensure that your website is compatible with the changes you want to make to your web hosting plan’s configuration**. Contact a [specialist provider](https://partner.ovhcloud.com/en-gb/directory/) if you have any doubts or encounter any difficulties.
>

#### 1.1 - Runtime environments <a name="runtime-environment"></a>

Runtime environments contain a set of programming languages. Depending on the chosen runtime environment, the languages are available in more or less advanced versions. The purpose of these environments is to allow you to correctly run the files that make up your website, in line with your technical needs.

On OVHcloud web hosting plans, we offer **3** runtime environments: *Legacy*, *Stable* and *Stable64*.
Below are the elements contained in our different runtime environments:

|Environment|Legacy|Stable|Stable64|
|---|---|---|---|
|Architecture|32-bit|32-bit|64-bit|
|Minimum PHP version|5.4|5.4|7.4|
|OpenSSL|1.0.1t|1.0.1t|1.1.1n|
|Python|2.7 and 3.4|2.7 and 3.7|2.7 and 3.7|
|Ruby|2.1|2.1|2.5|
|Rails|4.1|4.1|5.2|
|Perl|5.20|5.20|5.28|
|git|2.1|2.1|2.20|

> [!primary]
>
> The *Legacy* environment can be useful for older websites that still use old PHP versions. However, we strongly recommend using the *Stable64* environment, which has the latest updates. **Please ensure that your website is compatible before you make any changes.**
> 

#### 1.2 - PHP versions <a name="php-versions"></a>

PHP is a dynamic programming language used to build websites. For your website, depending on its age, the updates made, and certain variables required for it to work properly, you may need to change the PHP version it uses.

There are several versions of the PHP programming language. Version upgrades provide various patches and add or remove features. OVHcloud offers the latest major versions of PHP, a list of which can be found [here](https://www.ovhcloud.com/en-gb/web-hosting/uc-programming-language/).

Some PHP versions only work with certain runtime environments. Below are the PHP versions available on OVHcloud web hosting plans and compatible [runtime environments](#runtime-environment):

|PHP Versions|Compatible runtime environments|
|---|---|
|5.4, 5.5, 5.6, and 7.0|Legacy, Stable|
|7.1, 7.2, and 7.3|Stable|
|7.4, 8.0, 8.1, and 8.2|stable64|

> [!primary]
>
> Since some features may not be maintained with newer versions, **please ensure that the new PHP version you want is compatible with your website before you start making any changes.**
>

Although OVHcloud manages the installation of the latest PHP versions on its servers, you are responsible for ensuring that your website is **always up-to-date** and compatible with the latest PHP versions. There are two ways of doing this, depending on which website you are using:

**Case 1 - you are using a Content Management System (CMS)** such as *WordPress*, *Joomla!*, *PrestaShop* or *Drupal*: 

- Consult the official documentation created by the publisher of the CMS you are using.
- Take note of the information concerning the technical requirements for your CMS to work, as well as the changes you need to make in order to update it.
- If necessary, update your CMS by ensuring that the new version is compatible with OVHcloud web hosting.

**Case 2 - you are using a website based on a custom solution**: 

- Get in touch with the webmaster who created the website.
- Use the [official PHP documentation](http://php.net/manual/en/appendices.php){.external} , which provides more information on version migrations.
- If necessary, update your website’s code, ensuring that it remains compatible with OVHcloud web hosting.

If you need to, you can find out which PHP version is currently used by your web hosting plan in two ways:

- **Via the OVHcloud Control Panel**. Log in to the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.co.uk/&ovhSubsidiary=GB){.external} , then go to the `Web Cloud`{.action} section. In the left-hand column, click `Hosting plans`{.action} , then select the Web Hosting plan concerned. In the `General information`{.action} tab, find the version below *Global PHP version*. 

![phpversion](images/change-php-version-step1.png){.thumbnail}

> [!primary]
> If a blue round symbol is present, wait a few minutes for the version to update.
>

- **Via a script**. Create a **.php** script containing only the following code:

```php
<?php phpinfo(); ?>
```

Then put it online in your [FTP storage space](/pages/web_cloud/web_hosting/ftp_connection), then call it by accessing its full address/URL.

> [!warning]
>
> You can no longer modify the PHP version via a .htaccess file on the latest [OVHcloud Web Hosting](https://www.ovhcloud.com/en-gb/web-hosting/) solutions.<br>
> The command to change the PHP version in the .htaccess file does not allow us to use recent PHP versions on our infrastructure.
> You must use the .ovhconfig file.
>

#### 1.3 - PHP runtime environments <a name="php-runtime"></a>

PHP runtime software applications are programs that allow you to perform actions on the web server in a given way. Generally, this setting is modified to influence the speed at which requests generated by visitors to your website are executed.

On OVHcloud web hosting plans, we offer **2** PHP runtime environments: *php* (“PHP-FPM”) and *phpcgi*.

By choosing the *php* engine, you can enable or disable the PHP accelerator (PHP-FPM). This has been adapted to suit our infrastructure, with the aim of speeding up the execution speed of PHP scripts. 

The *phpcgi* engine executes requests “in series”, unlike the *php* (“PHP-FPM”) engine, which executes them “in parallel”.

In comparison, the PHP accelerator (PHP-FPM) offers up to seven times faster performance than using the *phpcgi* engine. 

#### 1.4 - Application firewall <a name="firewall"></a>

A firewall is a type of security that filters incoming requests from your web hosting plan. On our web hosting plans, this configuration setting works as an **activable** or **deactivable** option.
This is because you will not be able to change the firewall filtering settings per se.

Please refer to our guide “[Activating the application firewall](/pages/web_cloud/web_hosting/multisites_activating_application_firewall)” for more details on this topic.

> [!warning]
>
> If you use payment modules, enabling the application firewall can sometimes cause communication disruptions between the payment module and the banks. If this is the case, deselect the option.
>

#### 1.5 - Execution modes <a name="runtime-mod"></a>

The execution modes allow you to manage the cache behavior of your website's static files (images, for example) as well as the processing of PHP errors (generally useful when your website displays a blank page, for example). 

There are **2** modes that you can enable: *Production* and *Development*.

|Mode|Static File Cache|Processing PHP Errors|
|---|---|---|
|*Production*|Maximizes caching of static files on web browsers.|PHP errors do not appear on your website.|
|*Development*|No cache is applied.|PHP errors will appear on your website.|

> [!primary]
>
> For PHP versions 7.1 and later, errors will appear on the website, regardless of the mode used. 
> 

Now that you know the different editable settings for your OVHcloud Web Hosting plan, learn about the two methods for changing these settings.

### 2 - Method 1: Modify the web hosting plan configuration via the OVHcloud Control Panel <a name="setting-ovh-manager"></a>

> [!warning]
>
> As a reminder, changing at least one of these elements may affect the display or the proper functioning of your website. **Please ensure that your website is compatible with the changes you want to make to your web hosting plan’s configuration.** If you have any doubts, or encounter any difficulties, please contact a [specialist provider](https://partner.ovhcloud.com/en-gb/directory/).
>

#### 2.1 - Access Web Hosting plan configuration management

Log in to your [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.co.uk/&ovhSubsidiary=GB){.external} , then go to the `Web Cloud`{.action} section. In the left-hand column, click `Hosting plans`{.action} , then select the Web Hosting plan concerned. Make sure you are positioned on the tab
`General information`{.action}. On the right-hand side of the note `Global PHP version`{.action} located almost in the center of the page, click the `...`{.action} button, then `Modify configuration`{.action}.

![hostingconfiguration](images/change-hosting-configuration-step1.png){.thumbnail}

> [!primary]
>
> If the `Modify configuration`{.action} button is grayed out, it may be that the **global PHP version** is being verified. If this is the case, a blue round symbol will appear next to the version, indicating that a check is in progress. Then wait a few minutes for the `Modify configuration`{.action} button to become accessible again.
>
> If the `Global PHP version`{.action} option does not appear in your [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.co.uk/&ovhSubsidiary=GB), check that the *.ovhconfig* file exists in the FTP root of your OVHcloud web hosting plan.
>
> Find all the information about the *.ovhconfig* file in the third part “[Method 2: Modify your Web Hosting plan’s configuration from the “.ovhconfig” file](#setting-ovhconfig)” of this guide.
>

#### 2.2 - Modify your web hosting plan’s configuration

In the window that pops up, you can choose between two options. Select the one that corresponds to the action you want to carry out, then click `Next`{.action}.

|Choice|Detail|
|---|---|
|`Return to a previous configuration`|After selecting this option, choose the configuration to restore next to `Historical choice`. This option may not be available if you have not made any changes in the past.|
|`Modify the current configuration`|After you select this option, choose the modifications you want to make to the configuration from the fields provided. If necessary, go back to the first part “[Description of the configuration settings available on OVHcloud web hosting plans](#all-parameters)” of this guide.|

> [!primary]
>
> Changing the runtime environment of your web hosting plan automatically resets PHP sessions.
> 

Once you are ready, click `Confirm`{.action} to apply the modification. Wait a few moments for the process to complete.

![hostingconfiguration](images/change-hosting-configuration-step3.png){.thumbnail}

### 3 - Method 2: Modify the web hosting plan configuration from the ".ovhconfig" file <a name="setting-ovhconfig"></a>

#### 3.1 - Log in to your web hosting plan’s FTP storage space

Get your primary FTP username, its password, and the FTP server address.
To do this, log in to your [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.co.uk/&ovhSubsidiary=GB){.external} , then go to the `Web Cloud`{.action} section. In the left-hand column, click `Hosting plans`{.action} , then select the web hosting plan concerned. Go to the `FTP - SSH`{.action} tab. Here, you will find the information you need to log in. 

For the FTP user password, please refer to our guide on [Modifying an FTP user password](/pages/web_cloud/web_hosting/ftp_change_password) if required.

![ovhconfig](images/ovhconfig-step1.png){.thumbnail}

#### 3.2 - Retrieve or create the .ovhconfig file

Once you have logged in to your [FTP storage space](/pages/web_cloud/web_hosting/ftp_connection), you can view all of the files currently hosted on it. Stay positioned on the root of your hosting (which can be symbolized by a “ /”). You should find the .ovhconfig file there.

![ovhconfig](images/ovhconfig-step2.png){.thumbnail}

There are two ways of doing this:

- **the .ovhconfig file is there** : download it to your own machine/device. Make a copy of it before editing it. This will allow you to restore the original file if necessary.
- **The .ovhconfig file does not exist** : create it on your own machine/device and name it ".ovhconfig".

#### 3.3 - Edit the contents of the ".ovhconfig" file <a name="update-ovhconfig"></a>

Once you have the .ovhconfig file, edit it. To do this, use a program such as a text editor. Your ".ovhconfig" file must contain a code similar to the following:

```php
app.engine=php
app.engine.version=8.0

http.firewall=none
environment=production

container.image=stable64
```

> [!success]
>
> If you have just created the .ovhconfig file, copy the code above into your file, then continue reading this guide.
>

Customize the values of the variables depending on the configuration you want to use with your web hosting plan.

|Variables|Detail|
|---|---|
|app.engine|Allows you to modify [the PHP engine](#php-runtime) used by the hosting system. Enter **php** to enable the PHP-FPM accelerator, and **phpcgi** to disable it.|
|app.engine.version|Allows you to define [the PHP version](#php-versions) used by the hosting plan among [the ones OVHcloud offers](https://www.ovhcloud.com/en-gb/web-hosting/uc-programming-language/){.external}. Enter the version of your choice (appropriate for the runtime environment you have chosen to use).|
|http.firewall|Enables or disables the [firewall supplied with OVHcloud web hosting plans](https://www.ovhcloud.com/en-gb/web-hosting/options/){.external}. Enter **security** to enable it, or **none** to disable it.|
|environment|Allows you to manage the behavior of your website's static file cache, as well as PHP error processing. This corresponds to [execution mode](#runtime-mod). Enter **production** to maximize caching and hide PHP errors, or **development** so that no cache is applied and PHP errors are displayed.|
|container.image|Allows you to modify the [runtime environment](#runtime-environment) used by the hosting. Enter the runtime environment (**legacy**,**stable** or **stable64**) of your choice. If you choose the **stable64** runtime environment, ensure that your site is compatible with 64-bit architecture.|

If you need to, go back to the first part “[Description of the configuration settings available on OVHcloud web hosting plans](#all-parameters)” of this guide.

If necessary, please find the detailed technical description of the .ovhconfig file below:

```php
; ovhconfig
;
; this file must be placed in $HOME/.ovhconfig or in $DOCUMENT_ROOT/.ovhconfig

; __app.engine__
;
; values: php (php engine + opcache accelerator)
; notice: if php, a phpcgi engine will be activated as fallback (if previous engine crash)
;
;   php:
;       IMPORTANT: register_globals and magic_quotes_gpc are off for security
;       php optiones .htaccess (like php version) are ignored
;   phpcgi:
;       IMPORTANT this is a fallback to previous system
;       in this case __app.engine.version__ will be considerated as AUTO and php version will be old system
;       (meaning depending .htaccess or .phpX extension)
;
app.engine=php

; __app.engine.version__ specify version of your engine
;
; for php:
;   default: 8.0
; for phpcgi:
;   this options is ignored (= fallback in AUTO)
;
app.engine.version=8.0

; __http.firewall__ used to add application firewall  (filter http requests)
;
; values: none | security
; default: none
;
http.firewall=none

; __environment__
;
; values: production | development
;
;   production:
;       apache will maximise local cache
;       mod_expires will grow up TTL of js, css, pdf, images, video, audio
;       you can override it changing expiration explicitly in your .htaccess
;       feel free to look on our guide.
;   development:
;       no expiration is added, files are not locally in cache,
;       will speed up tests but decrease performances
;
; choosen environment will also be available in your variable ENVIRONMENT unix env
;
; default: production
;
environment=production

; __container.image__
;
; values: legacy | stable | stable64
;
container.image=stable64
```

#### 3.4 - Download the ".ovhconfig" file to the storage space

Once you have modified the .ovhconfig file, download it to your [FTP storage space](/pages/web_cloud/web_hosting/ftp_connection). To do this, reconnect to your [FTP storage space](/pages/web_cloud/web_hosting/ftp_connection) and go to the root of your [FTP storage space](/pages/web_cloud/web_hosting/ftp_connection) (which can be represented by a “ /”). Upload the .ovhconfig file you have just edited to your [FTP storage space](/pages/web_cloud/web_hosting/ftp_connection). If the file already exists, replace it.

### 4 - Advanced use of .ovhconfig files <a name="ovhconfig-more"></a>

If you use your web hosting plan to host several websites on it (in *multisites*), there are various reasons why you may want to use a different PHP version for some of your *multisites*.

Create a .ovhconfig file containing the PHP version you want for the *multisites* concerned. Use the instructions in the [3.3 - Modify the content of the .ovhconfig file](#update-ovhconfig) section of this guide, if required. When you upload the .ovhconfig file to your [FTP storage space](/pages/web_cloud/web_hosting/ftp_connection), do so in the root folder where the files that make up the relevant "*multisites*" website are located. You can find the root folder of your *multisites* in your [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.co.uk/&ovhSubsidiary=GB) in the `Multisite`{.action} tab of the Web Hosting plan concerned.

Refer to our guide on Configuring a multisite on your web hosting plan (/pages/web_cloud/web_hosting/multisites_configure_multisite) , if required.

> [!warning]
>
> **You cannot specify a second [runtime environment](#runtime-environment), a second [runtime mode](#runtime-mod) and/or a second [PHP runtime environment](#php-runtime)** on the same web hosting plan. Only those entered in the .ovhconfig file located in the root of your [FTP storage space](/pages/web_cloud/web_hosting/ftp_connection) will be taken into account.
>

![ovhconfig](images/ovhconfig-step3.png){.thumbnail}

## Go further

[Log in to your Web Hosting plan’s storage space](/pages/web_cloud/web_hosting/ftp_connection)

For specialised services (SEO, development, etc.), contact [OVHcloud partners](https://partner.ovhcloud.com/en-gb/directory/).

If you would like assistance using and configuring your OVHcloud solutions, please refer to our [support offers](https://www.ovhcloud.com/en-gb/support-levels/).

Join our community of users on <https://community.ovh.com/en/>. 