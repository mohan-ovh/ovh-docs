---
title: AI Training - Manage Docker registries
excerpt: Learn how to add your own registry to AI Training via UI
routes:
    canonical: '/pages/public_cloud/ai_machine_learning/training_guide_05_howto_add_registry'
updated: 2023-05-11
---


## Objective

This guide covers the process of adding a private registry to the **AI Training** service.

## Requirements

-   a **Public Cloud** project
-   credentials for the Docker registry you wish to add
-   access to the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl)

## Instructions

### Step 1: Going to the AI Training menu

Log in to the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl), go to the `Public Cloud`{.action} section, then to the `AI Training` section which is located under `AI & Machine Learning`.

![image](images/00_training_menu.png){.thumbnail}

From the dashboard you can add your Docker registry by clicking `Private Docker Registry`{.action} > `Add`{.action} button.

### Step 2: Adding the registry

To add a registry you simply need to provide the credentials of your registry along with its URL.

![add registry form](images/01_add_registry_form.png){.thumbnail}

Once the form is filled out click `Add`{.action}.

### Step 3: Submitting an image from your registry

Once your registry is added you can use any images pushed on the registry for your jobs.

From the OVHcloud Control Panel while [submitting a job](/pages/public_cloud/ai_machine_learning/training_guide_02_howto_submit_job), you can choose a custom Docker image in Step 2.

![custom docker image](images/02_submit_image_custom.png){.thumbnail}

With the `ovhai` command line CLI simply provide the image with `ovhai job run <image>`.

The default shared registry remains available even with a private registry added.

## Going Further

-   You can check the official documentation about [how to submit a **job**](/pages/public_cloud/ai_machine_learning/training_guide_02_howto_submit_job)
-   You can check out the documentation about the [`ovhai` CLI](/pages/public_cloud/ai_machine_learning/cli_15_commands_reference)
-   You can check out the documentation about [how to setup the `ovhai` CLI](/pages/public_cloud/ai_machine_learning/cli_10_howto_install_cli)

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](https://www.ovhcloud.com/pl/professional-services/) to get a quote and ask our Professional Services experts for a custom analysis of your project.

## Feedback

Please send us your questions, feedback and suggestions to improve the service:

- On the OVHcloud [Discord server](https://discord.com/invite/vXVurFfwe9) 
