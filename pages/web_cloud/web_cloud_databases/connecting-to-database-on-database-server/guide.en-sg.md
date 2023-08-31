---
title: 'Connecting to a database on your database server'
excerpt: 'Find out how to log in to your database'
updated: 2023-06-22
---

## Objective

You can access your database’s content via an interface. There are several ways you can connect to it.

**This guide explains how to connect to your database on your database server.**

## Requirements

- You must have a [Web Cloud Databases instance](https://www.ovh.ie/cloud-databases/){.external} (included in a [Performance web hosting plan](https://www.ovhcloud.com/en-sg/web-hosting/)).
- access to the [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/sg/&ovhSubsidiary=sg)

## Instructions

> [!primary]
>
> Please note that the [Web Cloud Databases](https://www.ovh.ie/cloud-databases/){.external} solutions do not give access to the database management system, but to the databases hosted on it.
> <br> - Please note that there is no "root" access.
> <br> - Generic SQL commands work normally, and software such as HeidiSQL, SQuirreL or Adminer is fully compatible.
> 

### Logging in to a MySQL or MariaDB database 

> [!primary]
>
> Since MariaDB is a derivative of MySQL, the commands are exactly the same for these 2 types of databases.
> 

####  With OVHcloud phpMyAdmin

Log in to your [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/sg/&ovhSubsidiary=sg) and select `Web Cloud`{.action} in the top navigation bar. Click `Web Cloud Databases`{.action}, then choose the SQL instance concerned.

In the `General information` tab, you will find the access link in the **Database administration** box, under “User interface”.

![private-sql](images/private-sql-phpma01.png){.thumbnail}

You will land on the phpMyAdmin login page.

![private-sql](images/private-sql-phpma02.png){.thumbnail}

- **Server and port**: Enter the host name and port of your server, which you can view in the `General information` tab, in the **Database administration** box, under “Host name” and ”Port” in the **SQL** section. The host name and port must be separated by a space.
- **User**: Enter the username you created in the `Users and rights` tab of your database server.
- **Password**: Enter the password for the user concerned.

If the connection succeeds, the next page of phpMyAdmin will appear.

![private-sql](images/private-sql-phpma03.png){.thumbnail}

> [!warning]
>
> **In case of error :**
> <br> - Error #1045, it means that the identification is incorrect. You will need to check your username and/or password.
> <br> - Error #2005, we recommend checking the server name, and whether it is working properly.
>

#### Connecting to the database outside the Control Panel

> [!warning]
>
> If you use a `Web Cloud Databases` or `Private SQL` service, do not forget to authorise your IP address using the guide on [Configuring your database server](/pages/web_cloud/web_cloud_databases/configure-database-server).
>

To connect to your database, please ensure that you have the following information:

- **Server**: the host name of your server is visible in the `General information` tab of your database server, in the **Database administration** box under “Host name” in the **SQL** section.
- **User**: The user name you created in the `Users and rights` tab of your database server.
- **Password**: The password associated with the connecting user.
- **Port**: The port is visible in the `General information` tab of your database server, in the **Database administration** box, under “Port” in the **SQL** section.
- **Database Name:**: The databases are listed in the `Databases` tab of your database server.

##### 1\. Connecting via the command line

```bash
mysql --host=server --user=username --port=port --password=password database_name
```

##### 2\. Connecting via PHP script

```php
1. <?php
2. $db = new PDO('mysql:host=host;port=port;dbname=dbname', 'username', 'password');
3. ?>
```

##### 3\. Connecting via software (SQuirreL)

> [!primary]
>
> In our example we use the open source software SQquirreL, but other interfaces like HeidiSQL or Adminer are fully compatible. 

- Launch SQuirreL and click `Aliases`{.action}, then `+`{.action}

![launch SQuirreL](images/1.png){.thumbnail}

- Fill in the fields below and confirm by clicking `OK`{.action}:
    - **Name**: Select a name.
    - **Driver**: Choose "MySQL Driver".
    - **URL**: Enter the server address and port as jdbc:mysql://server:port.
    - **User Name**: Enter the username.
    - **Password**: Enter the password.

![config connection](images/2.png){.thumbnail}

- Confirm again with the `Connect`{.action} button.

![valid connection](images/3.png){.thumbnail}

You are now connected to your database.

![config connection](images/4.PNG){.thumbnail}

##### 4\. Connecting with phpMyAdmin

You can use your own phpMyAdmin interface to access the contents of your database. To do this, install phpMyAdmin on your own server or Web Hosting plan. During this installation, make sure that the information for your database server and database is correctly configured so that phpMyAdmin can connect to it.

### Logging in to a PostgreSQL database 

To connect to your database, please ensure that you have the following information:

- **Server**: the host name of your server is visible in the `General information` tab of your database server, in the **Database administration** box under “Host name” in the **SQL** section.
- **User**: The user name you created in the `Users and rights` tab of your database server.
- **Password**: The password associated with the connecting user.
- **Port**: The port is visible in the `General information` tab of your database server, in the **Database administration** box, under “Port” in the **SQL** section.
- **Database name**: The databases are listed in the `Databases` tab of your database server.

#### Connecting via the command line

```bash
psql --host=server --port=port --user=username --password=password database_name
```

#### Connecting via PHP script

```php
1. <?php
2. $myPDO = new PDO('pgsql:host=host;port=port;dbname=dbname', 'username', 'password');
3. ?>
```

#### Connecting via software (SQuirreL)

> [!primary]
>
> In our example we use the open-source software SQuirreL, but other interfaces like HeidiSQL or Adminer are fully compatible.

- Launch SQuirreL and click `Aliases`{.action}, then `+`{.action}

![launch SQuirreL](images/1.png){.thumbnail}

- Fill in the fields below and confirm by clicking `OK`{.action}:
    - **Name**: Select a name.
    - **Driver**: Choose "PostgreSQL".
    - **URL**: Enter the server address and port as jdbc:postgresql://server:port/database.
    - **User Name**: Enter the username.
    - **Password**: Enter the password.

![config connection](images/2.png){.thumbnail}

- Confirm again with the `Connect`{.action} button.

![valid connection](images/3.png){.thumbnail}

You are now connected to your database.

![config connection](images/4.PNG){.thumbnail}

## Go further

For specialised services (SEO, development, etc.), contact [OVHcloud partners](https://partner.ovhcloud.com/en-gb/).

If you would like assistance using and configuring your OVHcloud solutions, please refer to our [support offers](https://www.ovhcloud.com/en-sg/support-levels/).

Join our community of users on <https://community.ovh.com/en/>. 
