---
title: 'Technical specifications of Web Hostings'
excerpt: 'Find out more about the technical capabilities of your Web Hosting plan '
updated: 2022-11-18
---

## Objective

**This guide collects some technical details about the OVHcloud Web Hosting infrastructure, based on frequently asked questions.**

## Requirements

- an [OVHcloud Web Hosting plan](https://www.ovhcloud.com/en/web-hosting/)
- access to the [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/world/&ovhSubsidiary=we)

## Instructions

> [!warning]
>OVHcloud is providing you with services for which you are responsible, with regard to their configuration and management. You are therefore responsible for ensuring they function correctly.
>
>This guide is designed to assist you in common tasks as much as possible. Nevertheless, we recommend contacting a specialised provider and/or the software publisher for the service if you encounter any difficulties. We will not be able to assist you ourselves. You can find more information in the “Go further” section of this guide.
>

### FTP

- Access error ("530 Login authentication failed"): You can make sure the access credentials to your hosting space are correct by checking via the [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/world/&ovhSubsidiary=we) ("FTP - SSH"). Passwords are never displayed but they can be changed. Please refer to our [FTP guides](/products/web-cloud-hosting).

- FTP connections have to use **passive mode**. Please make sure your script or FTP client is adjusted accordingly.

### Emails <a name="emails"></a>

To guarantee a good quality of service for all and make it easier to send your emails to recipients, we apply quotas for our web hosting services.

For a rolling period of 3600 seconds (1 hour), your hosting plan will allow you to send the following email quotas:

|Offers|Personal|Pro|Performance|
|---|---|---|---|
|Maximum number of emails sent per hour per service|100|200|2000|

- Apart from suspected spamming or phishing, the sending of your emails may be delayed. Your emails will be kept in a queue until the number of emails sent in the last hour is less than the quota.
- In the event of abuse or proven risk, your service will be suspended and you will be notified by email of its suspension. What to do if your account is blocked for spam? Read [our guide](/pages/web_cloud/email_and_collaborative_solutions/troubleshooting/locked_for_spam).

### Databases / SQL

#### Simultaneous Database Connections

- On Web Hosting plans (shared databases), there is a limit of 30 concurrent connections per database. Plese refer to the [product page](https://www.ovhcloud.com/en/web-hosting/) to verify the available options of our Web Hosting plans.

#### Connections from an external server

- For security reasons it is not possible to connect from an external server to a Web Hosting plan's database. Only OVHcloud Web Hosting servers are able to connect to the database servers. Any other connection will cause the following error:

```bash
Warning: MySQL Connection Failed: Host ip.your.connection is not allowed to connect ...
```

#### Shared SQL server limitations

- Log in to the PhpMyAdmin interface and then enter **show variables** to verify the values of the MySQL server variables.

- The MySQL version cannot be changed for Web Hosting databases.

Please refer to [this guide](/pages/web_cloud/web_hosting/sql_create_database) for more information about managing databases.

### PHP

- We recommend to consult [our website](https://www.ovhcloud.com/en/web-hosting/uc-programming-language/) to make sure the Web Hosting plan you would like to order will be appropriate for your hosting requirements.

> [!warning]
>
> You cannot edit the **php.ini** file on shared hosting plans because the PHP configuration is global to the entire shared infrastructure.
>

- You can verify the details of the configuration on our website; please see under [Web Hosting libraries](./#web-hosting-libraries) below. 

- You will be able to change the PHP version for your Web Hosting, either in the [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/world/&ovhSubsidiary=we) ("**Configuration**") or by editing the .ovhconfig file. Mixed configurations are also possible with the latter. Detailed instructions are available in our guides:

[Configuring the .ovhconfig file of your Web Hosting plan](/pages/web_cloud/web_hosting/php_configure_php_on_your_web_hosting_2014)  
[Modifying the configuration of a Web Hosting plan](/pages/web_cloud/web_hosting/php_configure_php_on_your_web_hosting_2014)

> [!primary]
>
> The .ovhconfig file is functional at the root folder of the Web Hosting or in a level 1 subdirectory (usually _/www/_). The only way to override the main .ovhconfig settings is with another .ovhconfig file in a subfolder.  
Placing this file deeper in the directory structure will have no effect (e.g. _/www/test/_, _/www/test/test2/_). Make sure the file is readable by your CMS (604 or 644).
>

#### PHP-FPM

PHP-FPM is enabled by default on the Web Hosting infrastructure in order to speed up PHP responses. Please note that it might not be active if you are running an older version of a Web Hosting plan which you have not upgraded (services ordered before 2014).

*Some server variables are different without PHP-FPM:*

|Variable|without PHP-FPM|with PHP-FPM|
|---|---|---|
|max_execution_time|120s|165s|
|max_input_vars|2000|16000|
|memory_limit|128M|512M|

#### PHP scripts

Once you are connected to your hosting server via SSH, outgoing traffic will be blocked for security reasons. We therefore recommend to use PHP scripts. Please refer to our [SSH guide](/pages/web_cloud/web_hosting/ssh_on_webhosting) for more information. You can consult the official [PHP manual](https://www.php.net/manual/en/function.system.php) on how to execute commands and perform other tasks.

As an example, you can use the function *gethostbyaddr()* to retrieve the hostname:

```php
1. <?php
2. echo gethostbyaddr($_SERVER["REMOTE_ADDR"]);
3. ?>
```

> [!warning]
>OVHcloud does not force PHP updates. Customers are fully responsible for keeping their services secure and for ensuring that any installed software is updated regularly.
>

#### Web Hosting libraries

We recommend to consult the information pages to verify the available libraries for your Web Hosting plan. You can find your "infos" page by using the respective cluster link: <https://webhosting-infos.hosting.ovh.net>

To find out on which Web Hosting cluster your service is located, log in to your [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/world/&ovhSubsidiary=we) and select `Web Cloud`{.action}. Click `Hosting plans`{.action}, then choose the Web Hosting plan concerned. Next, navigate to the `FTP - SSH`{.action} tab.
You can verify the cluster number of the Web Hosting on this page under **FTP server**.

For CloudWeb Hostings, please refer to: <https://cloudweb-infos.hosting.ovh.net/>

### Automatic backup information <a name=“backup”></a>

> [!warning]
>
> OVHcloud is committed to providing an automatic data backup service, as well as making these backups available. However, it is your responsibility to set up your own restoration policy, and to determine restore points at times you deem appropriate.

### Disk space

All of our web hosting plans are located in:

- in Gravelines (GRA), in France, have automatic backups at D-1 / D-2 / D-3 / D-7 / D-14. These backups are also stored in the Roubaix (RBX) datacentre in France.

- in Beauharnois (BHS), Canada, have automatic backups at D-1 / D-2 / D-3 / D-7 / D-14. These backups are also stored in the Beauharnois (BHS) datacentre in Canada.

Find out how to [log in to your storage space](/pages/web_cloud/web_hosting/ftp_connection) or [restore your Web Hosting plan’s storage space](/pages/web_cloud/web_hosting/ftp_save_and_backup) in our documentation.

#### Database / SQL

For shared databases (included in your web hosting plan) or database servers (Web Cloud Databases), offered in Gravelines (GRA), France and Beauharnois (BHS), Canada, the databases are backed up every day. You can access these backups (via [the OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/world/&ovhSubsidiary=we){.external} or via the [OVHcloud API](https://api.ovh.com/)). Backups are also stored on another infrastructure. This data is replicated in 3 separate locations in France: Roubaix(RBX), Strasbourg(SBG), and Gravelines(GRA). The backup retention policy is 30 days.

Find out how to [Retrieve a database backup of a Web Hosting plan](/pages/web_cloud/web_hosting/sql_database_export) in our guide.

#### Email

For shared email accounts (included in your Web Hosting plan), a daily automatic backup is created and copied to another datacentre.

### Cookie Policy

**Cookies and trackers used in the provision of the Shared Hosting service.**

In order to ensure the proper functioning of websites hosted on the Shared Hosting service, a "SERVER ID" cookie for those websites is placed on the end user's device. The "SERVER ID" cookie enables a service for allocating incoming traffic between the different infrastructures used for hosting the website (OVHcloud Load Balancer). It allows the user to stay on the same host server for the duration of the session. This helps to maintains and preserve the consistency of the user experience.

The "SERVER ID" cookie is a file stored on the end user's device that indicates the instance (server) of the infrastructure with which the user interacts. The cookie is anonymous in that no personal data of the user is processed.

The "SERVER ID" cookie is placed on the user's device for a period of less than 24 hours.

Based on the fact that this cookie is anonymous and is only necessary for the operation of the Shared Hosting service, it is not liable to the prior consent of the website visitor within the meaning of the General Data Protection Regulation (GDPR).

### Information about statistical tools

**OVHcloud Web Statistics**

OVHcloud makes available to the client statistics on website visitors and audience measurement of the website(s) hosted as part of the Hosting service(s) (hereinafter "OVHcloud Web Statistics"). OVHcloud Web Statistics helps to identify the geographical area of users of these websites, the characteristics of the devices used to access the website(s), the page views and HTTP codes. OVHcloud Web Statistics is enabled by default as part of the Shared Hosting service and can be readily disabled at the customer's request by contacting the technical support. In order to provide "OVHcloud Web Statistics", OVHcloud performs data processing.

OVHcloud Web Statistics reports are compiled from anonymised traffic data, such as the IP address and logs of users of the website, the url of the request, the duration of the request and the "user agent".

In order to be used as part of OVHcloud Web Statistics Statistics, the aforementioned data is anonymised and aggregated using algorithms operated by OVHcloud on its own infrastructure. In particular, in order to be processed and analysed to determine the geolocation of the user (limited to a region), the IP address of the user, present in the above mentioned traffic data, is extracted in anonymised form. Thus, no personal data allowing the identification, direct or indirect, of the website users is stored as part of OVHcloud Web Statistics.

## Go further

[Logging in to your Web Hosting plan’s storage space](/pages/web_cloud/web_hosting/ftp_connection)

[Activating HTTPS on your website with an SSL certificate](/pages/web_cloud/web_hosting/ssl-activate-https-website)

[Optimise your website’s performance](/pages/web_cloud/web_hosting/optimise_your_website_performance)

Join our community of users on <https://community.ovh.com/en/>.

