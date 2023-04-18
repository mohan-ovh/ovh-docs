---
title: Getting started with Public Cloud Databases
excerpt: Find out how to set up your managed database service in the OVHcloud Control Panel
routes:
    canonical: '/pages/platform/databases/databases_01_order_control_panel'
updated: 2022-07-27
---

**Last updated 15th February 2023**

## Objective

OVHcloud Databases as-a-service (DBaaS) allow you to focus on building and deploying cloud applications while OVHcloud takes care of the database infrastructure and maintenance.

**This guide explains how to order a database solution in the OVHcloud Control Panel.**

## Requirements

- Access to the [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/world/&ovhSubsidiary=ws)
- A [Public Cloud project](https://www.ovhcloud.com/es/public-cloud/) in your OVHcloud account

## Instructions

### Subscribing to the service

Log in to your [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/world/&ovhSubsidiary=ws) and switch to the `Public Cloud`{.action} section. After selecting your Public Cloud project, click on `Databases`{.action} in the left-hand navigation bar under **Storage**.

Click on the button `Create a database instance`{.action}. (`Create a service`{.action} if your project already contains databases.)

#### Step 1: Select your database type

Click on the type of database you want to use and then select the version to install from the respective drop-down menu.

![Choose database](images/databases_01_order_control_panel-20220727191054615.png){.thumbnail}

#### Step 2: Select a solution

In this step, choose an appropriate service plan. You will be able to upgrade the plan after creation.

![Choose plan](images/databases_01_order_control_panel-2022072719143198.png){.thumbnail}

Please visit the [capabilities page](https://docs.ovh.com/us/es/publiccloud/databases/) of your selected database type for detailed information on each plan's properties.

#### Step 3: Select a location

Choose the geographical region of the data centre in which your database will be hosted.

![Choose region](images/databases_01_order_control_panel-20220727191537259.png){.thumbnail}

#### Step 4: Configure database nodes

You can increase the number of nodes and choose the node model in this step. The initial and maximum numbers of nodes depends on the solution chosen in step 2.

![Order nodes](images/databases_01_order_control_panel-2022072719164714.png){.thumbnail}

Please visit the [capabilities page](https://docs.ovh.com/us/es/publiccloud/databases/) of your selected database type for detailed information on the hardware resources and other properties of the database installation.

Take note of the pricing information.

### Step 5: Size of nodes

Select the number of nodes required for your cluster:

![Size of nodes](images/databases_01_order_control_panel-20221214083133668.png){.thumbnail}

### Step 6: Configure your options

Depending on the type of database you can adjust the number of nodes in your cluster and add storage space:

![Cluster sizing](images/databases_01_order_control_panel-20230215131801790.png){.thumbnail}

### Step 7: Database service configuration

Define your network configuration:

![Configure options](images/databases_01_order_control_panel-20220727191850299.png){.thumbnail}

#### Connecting a private network (optional)

![Attach network](images/creation_mongo06.png){.thumbnail}

If you already have a private subnet available, check the box **Private** and select it from the drop-down menu. Note that this option might not be available for the selected service type.

You can be forwarded to create a private network or subnet by clicking on the respective links. You will have to start the database order process anew in that case.

Please follow [this guide](/pages/platform/network-services/getting-started-07-creating-vrack) for detailed instructions.

### Step 8: Summary and confirmation

The final section will display a summary of your order as well as the API equivalent of creating this database instance with the [OVHcloud API](/pages/account/api/first-steps).

![Confirm order](images/databases_01_order_control_panel-20220727192153640.png){.thumbnail}

Within a few minutes your new database service will be deployed. Messages in the OVHcloud Control Panel will inform you when the database is ready to use.

Continue with the *Configure your instance to accept incoming connections* guide of your selected database type available [here](https://docs.ovh.com/us/es/publiccloud/databases/) to configure your service after installation.

Note that the configuration options might be different, depending on the database type. You will find example on this repository: <https://github.com/ovh/public-cloud-databases-examples>.

## We want your feedback!

Visit our dedicated Discord channel: <https://discord.gg/PwPqWUpN8G>. Ask questions, provide feedback and interact directly with the team that builds our databases services.

Join our community of users on <https://community.ovh.com/en/>.
